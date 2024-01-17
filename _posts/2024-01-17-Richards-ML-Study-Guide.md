---
layout: post
title: Richard's ML Study Guide
subtitle: A collection of study materials for machine learning.
cover-img: /assets/img/humanoid_robot_in_a_cap_and_gown.png
thumbnail-img: /assets/img/humanoid_robot_post_it.png
share-img: /assets/img/humanoid_robot_in_a_cap_and_gown.png
tags: [code]
comments: true
---

I've been asked a few times for recommendations on how to get started studying machine learning. I am sharing it here for anyone who is interested, and I will update it as I find new resources.
This guide is meant for people with little to no experience.

# Math

## Linear Algebra

The most important math for machine learning is linear algebra. I recommend the following resources:

### ["Essence of linear algebra" 3Blue1Brown playlist](https://www.youtube.com/watch?v=fNk_zzaMoSs&list=PLZHQObOWTQDPD3MizzM2xVFitgF8hE_ab&index=1)

This is an excellent playlist that focuses on building intuition for linear algebra. It purposefully avoids computation and instead focuses on the geometric interpretation of linear algebra. I recommend watching this playlist before taking a linear algebra course.

### [Gilbert Strang's lectures on Linear Algebra](https://www.youtube.com/watch?v=ZK3O402wf1c&list=PL49CF3715CB9EF31D&index=1)



Gilbert Strang is a legendary MIT professor. This was one of the original courses posted to MIT OpenCourseWare and is still one of the best. It is a full course on linear algebra, and it is a great resource for learning the computational side of linear algebra. I recommend watching this playlist after watching the 3Blue1Brown playlist. 

## Probability and Statistics

The second most import math for ML is probability and statistics. I recommend the following resources:

### ["Bayes theorem, the geometry of changing beliefs" by 3Blue1Brown](https://www.youtube.com/watch?v=HZGCoVF3YvM)

This video is a great introduction to Bayes theorem, one of the most important formulas in statistics. It breaks down each part of the formula, why is it true (visually), and when is it useful.

### ["An Introduction to Statistical Learning: with Applications in Python" by James et al.](https://www.statlearning.com/)



This is an excellent book for the foundations of statistics and ML. It is one of the most advanced resources on this list. It is a full book, so it is a big time commitment. It is free to read online and also comes with Python code examples. It covers a broad range of topics, including linear regression, logistic regression, decision trees, random forests, support vector machines, neural networks, clustering, and more.

The first edition of this book, ICLR, covers the same material but is for the R programming language. I definitely recommend the new Python version, ISLP.

## Calculus

The third most important math for ML is calculus. It is the basis for understanding backpropagation.

### ["Essence of calculus" 3Blue1Brown playlist](https://www.youtube.com/watch?v=WUvTyaaNkzM&list=PLZHQObOWTQDMsr9K-rj53DwVRMYO3t5Yr&index=1)


This is another excellent series from 3Blue1Brown. It focuses on building intuition for calculus, building up using thought experiments in a way that makes you feel like you are discovering calculus for yourself. Like his "Essence of Linear Algebra" playlist, it focuses on intuition rather than computation. I recommend watching this playlist before taking a calculus course.


### [Gilbert Strang's "Highlights of Calculus" playlist](https://www.youtube.com/playlist?list=PLBE9407EA64E2C318&index=1)



Another excellent playlist from Gilbert Strang. This is a more advanced playlist but it is still not a full course. It is a great resource for building intuition for calculus. I recommend watching this playlist after watching the 3Blue1Brown playlist.



# Programming

## Python

Python is the most popular language for machine learning. This is really the only language you need to know. I recommend the following resources:

### ["Automate the Boring Stuff with Python" by Al Sweigart](https://automatetheboringstuff.com/)



I believe that the best way to learn anything is with project-based learning. The nice thing about project-based learning is that you it helps you stay motivated to learn because you are working towards a tangible goal.
I recommend this book because each chapter is a project that gives you a useful tool that you can use in your daily life. I think everyone should read it for basic programming literacy.

It is also free to read online.

### [Codecademy Python 3 course](https://www.codecademy.com/learn/learn-python-3)



Codecademy is a nice because it gives you interactive programming challenges, and helps you learn by doing. This is a course you can complete in a few days and it will give you a good foundation in Python.

## Other languages

Some other languages that are popular for machine learning are R and Julia. 

Julia is a newer language purpose-built for machine learning, and it is gaining popularity. I think it is an elegant alternative to Python, but I can't recommend learning it because almost everyone uses Python. 

R is an older language that is popular in statistics. I really hate R, and I don't recommend learning it. It is a very ugly language, and it is not as generally useful as Python. It does, however, have a tremendous amount of statistical packages. If you are doing a lot of statistics, you may want to learn R. Otherwise, I recommend sticking with Python.

# Machine Learning

## ML Engineering

### ["Machine Learning Engineering for Production (MLOps)" course by Andrew Ng](https://www.youtube.com/playlist?list=PLkDaE6sCZn6GMoA0wbpJLi3t34Gd8l0aK&index=1)



This playlist focuses more on the engineering side of machine learning. For example, it covers common pitfalls and challenges when deploying ML models in production. I recommend this playlist for anyone working in an ML-adjacent role, as it gives you the bigger picture of the types of challenges with ML in production.

### ["A Recipe for Training Neural Networks" by Andrej Karpathy](https://karpathy.github.io/2019/04/25/recipe/)



This is a short blog post that gives some flavor of challenges in training neural networks, and why they are so difficult to diagnose as compared to other software systems.

The other blog posts on Andrej Karpathy's blog are also great.

### ["Hidden Technical Debt in Machine Learning Systems" by Sculley et al.](https://proceedings.neurips.cc/paper/2015/file/86df7dcfd896fcaf2674f757a2463eba-Paper.pdf)



This is a more academic paper that covers the challenges of ML systems in production, written by a team at Google.  One of the main points it makes is that only a small fraction of real-world ML systems are composed of actual ML code. The rest is data collection, data validation, feature extraction, serving infrastructure, monitoring, etc. This is a good paper to read if you want to understand the bigger picture of ML systems, and why they are so difficult to build.

### "Deep Learning" Coursera specialization by Andrew Ng

[Part 1](https://www.youtube.com/playlist?list=PLkDaE6sCZn6Ec-XTbcX1uRg2_u4xOEky0)

[Part 2](https://www.youtube.com/playlist?list=PLkDaE6sCZn6Hn0vK8co82zjQtt3T2Nkqc)

[Part 3](https://www.youtube.com/playlist?list=PLkDaE6sCZn6E7jZ9sN_xHwSHOdjUxUW_b)

[Part 4](https://www.youtube.com/playlist?list=PLkDaE6sCZn6Gl29AoE31iwdVwSG-KnDzF)

[Part 5](https://www.youtube.com/playlist?list=PLkDaE6sCZn6F6wUI9tvS_Gw1vaFAx6rd6)


This is the first course added to Coursera by Andrew Ng, and it is still one of the best. It is a great introduction to deep learning theory, and touches on the engineering side of ML as well. It is a bit dated, but it is still a great resource.

There is a new version of the course ("[Machine Learning Specialization](https://www.youtube.com/playlist?list=PLkDaE6sCZn6FNC6YRfRQc_FbeQrF8BwGI)"), but I haven't watched it yet.

### ["Data-centric ML" by Andrew Ng](https://www.youtube.com/watch?v=06-AZXmwHjo)


This is a short but influential talk by Andrew Ng that argues that there is an over-emphasis on model-centric ML, and that data-centric ML is more important. I recommend this talk for anyone who is interested in ML engineering as well as managers that work with ML teams.

There is an MIT course that is based on this talk: ["Data-Centric AI" course by MIT](https://github.com/dcai-course/dcai-lab)

## Deep Learning

### ["Neural networks" 3Blue1Brown playlist](https://www.youtube.com/playlist?list=PLZHQObOWTQDNU6R1_67000Dx_ZCJB-3pi&index=1)



This is a nice visual introduction to what is a neural network, as well as how backpropagation and gradient descent work.

### ["But what is a convolution?" by 3Blue1Brown](https://www.youtube.com/watch?v=KuXjwB4LzSA)



Convolutions are a key component of convolutional neural networks, which are the most popular type of neural network for computer vision. This is a nice visual introduction to what is a convolution.


### ["Visualizing Deep Learning" playlist by vcubingx](https://www.youtube.com/watch?v=UOvPeC8WOt8&list=PLyPKqVSnetmEOp_g_hfabuRAs9ET-shl_)


More visual intuition building for neural networks. This playlist is a bit more advanced than the 3Blue1Brown playlist, but it is still accessible for beginners.

### ["Neural Networks: Zero to Hero" playlist by Andrej Karpathy](https://www.youtube.com/playlist?list=PLAqhIrjkxbuWI23v9cThsA9GvCAUhRvKZ)

This playlist is a "hackers guide" to neural networks. It has an emphasis on coding everything from scratch in pure Python, so while the code is not the fastest it is compact, easy to read, and easy to understand. This is a great resource for learning how neural networks work under the hood end-to-end. I haven't watched the whole playlist, but I've watched a few videos and they were great and the code is very clean.

### ["Deep Learning" book by Ian Goodfellow et al.](https://www.deeplearningbook.org/)

This is an advanced book on deep learning theory. I've mostly read select chapters in Part 2 and Part 3, and it was great. It is free to read online.


### ["NYU Deep Learning" course by Yann LeCun and Alfredo Canziani](https://www.youtube.com/playlist?list=PLLHTzKZzVU9e6xUfG10TkTWApKSZCzuBI)


This is a full course on deep learning taught at NYU during COVID. It is a great resource for learning the theory of deep learning. It is a bit more advanced than the Andrew Ng course, but it is still accessible for beginners.


Alfredo Canziani also is [currently writing a book on deep learning theory](https://atcold.github.io/book.html) from an energy perspective. As of right now, it is not finished, but I am excited for it based on the sneak-peaks he has posted on Twitter.


### ["The Little Book of Deep Learning" by François Fleuret](https://fleuret.org/francois/lbdl.html)



This is a short but dense book on deep learning theory (150 pages). I haven't finished reading it but it has very nice visualization and explanations.

This book is available online for free or you can buy a physical copy for $10.

### [Distill.pub](https://distill.pub/)


Distill is a journal that publishes articles on machine learning. It aims to be a more visual, intuitive, and interactive vision of academic publishing for ML. The articles are extremely high quality and are a great resource for learning about advanced topics in ML. The articles have an emphasis on interpretability of ML models, deliving into the "black box" of neural networks by examining the behavior of specific circuits within the network.

One of the core Distill authors, Chris Olah, also [has a blog](http://colah.github.io/) with some legendary articles.

# Advanced Research

The best way to learn about advanced topics in ML is to read papers. I recommend the following resources for finding papers:

* [arXiv Sanity Preserver](http://www.arxiv-sanity.com/)
* Twitter. I find Twitter to be much better than Reddit for keeping up with the latest research. You can see who I follow [here](https://twitter.com/bae_theorem/following) (mostly computer vision researchers).
* [Semantic Scholar](https://www.semanticscholar.org/). Great for finding related papers.
