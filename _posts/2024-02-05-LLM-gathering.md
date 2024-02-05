---
layout: post
title: LLM Assistant for Better Gatherings
subtitle: Using a daisy chain of prompts to plan a potluck
cover-img: /assets/img/Bard-potluck.jpeg
thumbnail-img: /assets/img/Bard-potluck.jpeg
share-img: /assets/img/Bard-potluck.jpeg
tags: [code]
---

I wanted to share my work from an LLM hackathon hosted by [Deonna](https://github.com/deonna) and Nick from [AVL Digital Nomads](https://avldigitalnomads.org/). I recently have been reading *"[The Art of Gathering](https://www.priyaparker.com/book-art-of-gathering)"* by Priya Parker, which I recommend (see also: her [TED talk](https://www.ted.com/talks/priya_parker_3_steps_to_turn_everyday_get_togethers_into_transformative_gatherings) and [podcast](https://podcasts.apple.com/us/podcast/together-apart/id1506057555)). The goal was to create an assistant to help me brainstorm how to make events that are more meaningful and memorable.

In particular, I have an event template, I want to fill in each section of the template with the help of the LLM assistant. Here is the template:

```markdown
# The occasion

# What are the needs, specifically?
<fill in at least 3>

# What is the host's need? Why am I planning this event?

# Purpose of the event

### What is my need? Why am I the one planning this event?

# Who is the event for?
- *What are their needs in this specific moment?*
- *Which need will this gathering address?*

# Pop-up rules

# Size of the event

# Invitation

# Meaningful conversations

```

From experience, trying to fill in this template with an LLM assistant can be a bit of a mess. The LLM assistant can get off track, generate a bunch of nonsense, skip entire sections, and make up unwanted sections. 

To help with this, I made a daisy chain of prompts. Each prompt helps with a different aspect of event planning. I use the output of each chat session to build up my event plan, and use that growing event plan as the input to the next prompt/chat session. This helps to keep the collaboration with the LLM on the rails by constraining the output of the LLM. It also allows me to tell the LLM assistant when it's off track, and to guide it back in the right direction. Finally, I can clean up the output of each chat session before using it as the input to the next prompt/chat session.

I don't have a ChatGPT pro subscription, so instead I ended up using ChatGPT-4 API calls (specifically `gpt-4-turbo-preview`) via my note-taking app, [Obsidian](https://obsidian.md/). All of the prompts I use are available in my [LLM-gathering](https://github.com/crypdick/LLM-gathering/) repository.

# Throwing a Potluck

To demonstrate, let's try to throw a potluck using the LLM assistant. 

## Part 1: The purpose

I'll start by filling in the first section of the template:

```markdown
# The occasion

A potluck dinner at my house.
```

I then feed this into my first prompt ([step1-purpose](https://github.com/crypdick/LLM-gathering/blob/main/step1-purpose.md)). [Here is the raw output](https://gist.github.com/crypdick/88d97b19d69d511936e45f2d4d556a77). The summary was too wordy, so I replied `Please summarize the summary even further. Also, add something about promoting health in the purpose.` and I was mostly happy with that output. So, I edited it lightly and filled in the next section of the template:

```markdown
# Purpose of the event

* To strengthen community bonds and foster new connections in a shared, communal experience.
* To celebrate cultural diversity and promote understanding through a storytelling and cultural exchange centered around food.
* To encourage healthy eating by inviting participants to bring dishes that are not only personally significant but also reflect healthy food choices, enhancing the gathering's focus on well-being and communal health.
```

# Part 2: Who is the event for?

Next, I pasted in the what we have so far into the next prompt ([step2-who](https://github.com/crypdick/LLM-gathering/blob/main/step2-who.md)). The [raw output](https://gist.github.com/crypdick/0f3ccc5f5d11aebf49d9d3f082c159a4). Again, it was too wordy, so I slimmed it down. I dropped the desire to discuss healthy food choices, since it seems smug and I think we can just let the food speak for itself. I also excluded picky eaters, since they probably won't enjoy unfamiliar food.

```markdown
#### For
- People passionate about cultural diversity and willing to share their own cultural background through food.
- People interested in strengthening community bonds and making new connections.
- People who love trying new foods.

#### Not for
- People who are not respectful of or interested in other cultures.
- People who are not willing to participate in storytelling or cultural exchange.
- Those who are solely looking for a social event without engagement in the deeper purpose of the gathering.
- Picky eaters, or people with food allergies.
```

# Part 3: Pop-up Rules

The next prompt helps us to fill in the rules for the event ([step3-rules](https://github.com/crypdick/LLM-gathering/blob/main/step3-rules.md)) to promote inclusivity, equalization, and connection. These rules are meant to require no preparation from the guests. I didn't like most of the output, but it was a good starting point. I prompted it a few times to get more rules:

- `Please add something for people who want to bring a dish which is not necessarily significant in their culture. For example, they might want to bring a dish that honors a dead relative, or a dish connected to a story or a personal travel experience`
- `Make some additional rules to equalize the group. For example, not talking about careers. Also make some rules to increase inclusion and connections, such as only one person being allowed to speak at a time.`
- `Add rules for the following: you are not allowed to talk to the people sitting next to you, you have to talk to the whole table; avoid sitting next to people you know`

The full conversation [is here](https://gist.github.com/crypdick/7144849ee22d36ad00cffbf4fbb9d86f). Here are the rules I ended up with, which I organized into two sections: Inclusion and Connection.:

```markdown
# Rules for the event
## Inclusion

Rules to break cliques and equalize the group:

- **Dine and Switch**: Periodic seat swaps.
- **Stranger Danger**: Avoid sitting next to anyone you know.

## Connection

Rules to make everyone present, promote active listening, and foster deeper connections:

- **Profession Prohibition**: Avoid discussing professional life. This encourages focusing on personal interests, stories, and the cultural or emotional significance behind the dishes they've brought.
- **One Speaker at a Time**: Only one person is allowed to speak at a time. This encourages active listening, prevents interruptions, and ensures everyone is heard.
- **Dish Stories**: Each dish needs a story explaining its significance. This could include a memory of a loved one, an anecdote from a travel experience, sharing a cultural tradition, or a personal connection to the dish.
- **Global Flavor Challenge**: Guests are encouraged to try every dish.
- **Disconnect**: Please keep phones on silent and out of sight.
- **Culinary Compliments**: Before the end of the night, each guest must give a compliment to another guest about the dish they brought. This ensures everyone leaves feeling appreciated and connected.
- **The Connection Question Bowl**: Place a bowl filled with open-ended questions (e.g., "What's a food tradition you love in your culture?" or "Share a memory of your favorite meal and why it's significant to you.") at the center of the table. Guests can draw questions to answer or ask others, encouraging deeper conversations and connections.
```

# Part 4: Size of the event

The next prompt helps us to decide on the size of the event ([step4-size](https://github.com/crypdick/LLM-gathering/blob/main/step4-size.md)). This is a bit silly to ask the LLM, since the prompt gives granular guidelines, but I am lazy so I asked it anyway. [The output](https://gist.github.com/crypdick/3fb461bb62238ad2559a497886f418c6) was way too verbose just to say "12 to 15". 

```markdown
# Size of the event
12 to 15 guests
```

I am convinced OpenAI makes their LLMs excessively chatty, since they charge by the token.

# Part 5: Invitation

Finally, the fun part: the invitation. You can view the prompt [here](https://github.com/crypdick/LLM-gathering/blob/main/step5-invitation.md). I wasn't too happy with [the output](https://gist.github.com/crypdick/a2d0350b4a67eca79dcc60a49ac3aa9e), so I mixed it heavily with an invite I got from [a local event organizer](https://www.dylandavis.net/2023/09/salons-with-dylan/):


    # A Feast of Stories with Richard

    ## Purpose
    These potlucks at my home are more than just coming together to eat. They are special gatherings designed to foster meaningful conversations over our most universal language: food. The goal is to create a space where an intimate group can truly connect, share, and learn from each other's stories and experiences. We also aim to promote well-being through healthy diets.

    ## Why This Gathering?
    The intention behind these conversations is to curate a group that embodies traits like active listening, critical thinking, articulation, and vulnerability. It’s about creating a space where individuals can dive deep into conversations, bypassing the usual small talk. It's for curious souls, cultural explorers, and community builders.

    ## What to Expect?

    - *A Safe Space*: The gathering is a judgment-free zone that promotes open-mindedness and respect.

    - *Dish stories*: Each dish should have special significance to the person who brings it. This could include a memory of a loved one, a travel story, sharing a cultural tradition, or a personal connection to the dish.
    - *Commitment*: Please RSVP only if you are *sure* you can attend. If you must cancel, please inform at least 48 hours in advance.
    - *Limited Seats*: To maintain deep engagement, the gathering is limited to 15 attendees. This isn’t about exclusivity but about ensuring a meaningful experience. Attendees are chosen through a randomized raffle based on RSVPs.

    ## Rules

    These rules are designed to prevent cliques, equalize attendees, and foster deeper connections:

    - *Be Fully Present*: Phones should be out of sight.
    - *Active Listening*: Participants are encouraged to truly listen to one another and avoid interrupting.
    - *Active Participation*: While listening is important, so is active participation! Everyone should be prepared to share and engage.
    - *Made with love*: No fast food or store-bought dishes. Each dish should be homemade with love, or from an authentic restaurant.
    - *Periodic Seat Swaps*: We will switch seats to break cliques.
    - *Keep it personal*: Speak from your personal, lived experience. Avoid discussing professional life.
    - *No-shows*: If you RSVP and don't show up without notice, you will not be invited to future gatherings, out of respect for the community.

    ## Inspiration
    The rules are inspired by the book *The Art of Gathering* by Priya Parker, and by [Dylan's Salons](https://www.dylandavis.net/2023/09/salons-with-dylan/).



# Part 6: Meaningful conversations

I took some of the suggestions from the previous chat and used them to seed the next prompt ([step6-meaningful-convos.md](https://github.com/crypdick/LLM-gathering/blob/main/step6-meaningful-convos.md)):

```markdown
- **Dish Stories**: Each dish needs a story explaining its significance. This could include a memory of a loved one, an anecdote from a travel experience, sharing a cultural tradition, or a personal connection to the dish.
- **The Connection Question Bowl**: Place a bowl filled with open-ended questions (e.g., "What's a food tradition you love in your culture?" or "Share a memory of your favorite meal and why it's significant to you.") at the center of the table. Guests can draw questions to answer or ask others, encouraging deeper conversations and connections.
- **Culinary Compliments**: Before the end of the night, each guest must give a compliment to another guest about the dish they brought. This ensures everyone leaves feeling appreciated and connected.
```

The initial output had some ok, but I made a few additional idea requests:
- (after the first output) `I liked Kitchen Mishaps, Taste of Home, Recipe Wishlist, and Wellness Wins. Please come up with more conversation topics.`
- `Suggest a few conversation topics involving travel experiences`

Here is the [full chat](https://gist.github.com/crypdick/201fe370e44e70d217e252d6aac2880b). I didn't like most of the ideas, but I had enough materials to come up with some questions for the "connection question bowl":

```markdown
- **Kitchen Mishaps**: Share a story about a time you tried to cook a dish from another culture and it didn't go as planned. What did you learn from the experience?
- **Taste of Home**: What is one dish that instantly transports you back to your childhood or a cherished memory? Describe the sensory experience and the emotions it evokes.
- **Wellness Wins**: Discuss a small change you've made in your eating habits that had a big impact on your well-being. What motivated this change, and how has it influenced your lifestyle?
- **Culinary Challenges Conquered**: Talk about a dish that was challenging for you to master. What kept you motivated, and how did you feel when you finally got it right?
- **Comfort Foods with a Twist**: What's your go-to comfort food, and how have you made it your own?
- **Seasonal Sensations**: Discuss a food or dish that you associate with a particular season or holiday in your culture. How does this food contribute to your sense of belonging or celebration?
- **Cooking bucket list**: If you could take a cooking class in any country, where would you go and what would you want to learn
- **Potluck Perfection**: Recall a memorable dish someone else brought to a potluck that left a lasting impression on you.
- **Market Marvels**: Describe an unforgettable visit to a local market or street food vendor in another country. What sights, smells, and tastes stood out to you? How did this experience enhance your travel?
- **Dining Delights and Disasters**: Talk about your most memorable dining experience while traveling, whether it was delightfully surprising or a complete disaster. What made it so unforgettable?
```

# Conclusion

I made these prompts to make it easier for myself to host meaningful events in the future, and I hope you found them useful. If you have any suggestions for improvements to the prompts, please let me know. I would also love to hear about your experiences using the prompts to plan your own events.

Here are some tips:
- *Refine your prompt iteratively*. When you get a bad output, update your prompt so that future outputs are better.
- *Add examples to prompts*. This helps the LLM understand what you are asking for.
- *Break up your prompt into multiple parts*. This helps the LLM to focus on one aspect of the problem at a time.
- *Clear your chat history in between prompts*. LLMs have a limited context window, and start to forget the conversation once it gets too long. Conversely, old chat history can sometimes distract the LLM from the current problem.