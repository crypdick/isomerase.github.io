---
layout: post
title: In defense of Python assertions
tags: [code]
---

When new people join my team, I almost invariable hear feedback that Python assertions should be avoided. This might be a spicy take, but I disagree, provided that you use assertions correctly.

I use Python's `assert` statements a lot. I use it for debugging, for testing, and for documenting assumptions and expectations. 

Here is how I think assertions can be a useful tool for writing better code. But first, let me try to steelman the argument against assertions.


# The case against assertions 

Assertions have two downsides, which are valid. Later, I will explain how my usage of assertions mitigates these downsides.

## Assertions can be disabled

When you run Python in optimized mode (`python -O`), assertions are disabled. This is a big problem if your assertions are crucial for proper execution of your program.

Now, in my 10 years of Python programming, I have never heard of anyone using the `-O` flag. However, as a general principle, you shouldn't ever write something that a downstream team's decision to change interpreter flags can break your code.

## Assertions do not raise meaningful exceptions

It's true that `AssertionError` stacktraces are not super-informative.

# How I like to use assertions

## Design by Contract

[DbC](https://en.wikipedia.org/wiki/Design_by_contract) is a software engineering methodology that focuses on defining and enforcing specifications for software components. It does this with three main components:

* *Preconditions*: conditions that must be true before a function is called.
* *Postconditions*: conditions that must be true after a function is called.
* *Invariants* conditions that must be true throughout the execution of a function.

I use assertions is to document expectations about my code. I find this preferable than writing out the expectations in comments, since the assertions are executable. For example, if I have a function that takes a `DataFrame` as input, I might write:

```python
def fancy_processing(input_df: pd.DataFrame) -> pd.DataFrame:
    # Validate inputs
    assert list(input_df.columns) == sorted(input_df.columns), f"Columns should be sorted: {input_df.columns}"

    # do some processing

    # Validate outputs
    assert output_df.columns == input_df.columns, f"Columns should not change: {output_df.columns} != {input_df.columns}"
```

This is just an illustrative example. Don't go overboard exhaustively documenting every assumption, just whatever is useful for future maintainers. E.g. if I had `def double_col(df): df["col"] = df["col"] * 2` I wouldn't write `assert "col" in df.columns`.


There are some nice packages for Python DbC that I recommend:

* [Pydantic](https://docs.pydantic.dev/) for dataclasses
* [Beartype](https://beartype.readthedocs.io) for strict typing
* [Pandera](https://pandera.readthedocs.io) for validating DataFrames

I use assertions for DbC in ordinary functions. Yes, am aware of the [icontract](https://github.com/Parquery/icontract), but I find that it makes code less readable than using `@beartype` and assertions.

## Debugging

When I am quickly iterating on new code, I use assertions liberally as sanity checks to constrain the search space for bugs. For example, I might check that the shapes and dims of my tensors. This is especially useful when I'm working with a new codebase or when I'm working with a new library. Then, once I am ready to commit my code, I will prune some assertions which aren't helpful for future maintainers.


# When NOT to use assertions

Assertions should never be used to *handle errors which are likely to happen in production*. For example, avoid `try: ... except AssertionError: ...` block. Instead, use a `try: ... except MeaningfulException: ...` block to handle the error.

Another example is *sanitizing inputs*. If you are processing a user's input, [bad things can happen](https://xkcd.com/327/). You should always sanitize inputs, and thus you should never use an assertions which can be disabled.

I also delete assertions concerning PyTorch tensors that may be located on the GPU. This is because it will greatly slow down the code, since the GPU will have to move data to the CPU and wait for the assertion to be evaluated.