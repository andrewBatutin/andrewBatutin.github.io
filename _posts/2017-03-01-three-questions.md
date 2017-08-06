---
layout: post
title:  "3 main questions of Software Craftsmanship."
date:   2017-03-01 00:00:00
categories: project management
---

Introduction
------------
Have you ever find yourself in a situation when the email conversations are getting longer. And your commits are getting shorter? Have you ever been frustrated and annoyed by endless meetings and constant but unpredictable changes of the project's goals?
I did. And I'm not the project manager. I I'm not a product manager either. I'm not a manager at all. And I don't want to spend lion share of my time dealing with those issues.
So I've come up with not an answers but with questions to these matters.
Three short questions I always try to answer when the project gains its sideway trajectory.


_Assume team structure is a constant (you can't hire new or fire old people)_

Who are we?
-------------------
An essential question for every team. Without a clear understanding of what your team like it's really hard to match the expectations and reality.

You can ask yourself:

- How many of us are there?
- What's our level?
- What're our motives?

This question helps to understand your team, and its limitations and capabilities. If you are a bunch of JS guys and you'd love to work on embedded software system - that might be not the best of ideas.
As well as trying to put C++ dev with 15+ years of experience at Web dev shoes.


Where are we?
-------------------

Where we are is a fascinating question. Because it's related to a highly precious resource - time. It might make sense to rephrase this question to __When are we?__. But I'm afraid if you're going to ask your boss such question you won't stick to that job for long:)
It's essential to understand what type of product you're working on. And at what stage of development this product is. As well as trying to understand your company state.

Try to ask yourself next questions:

- Are we making a product?
- Are we doing it-consulting?
- Are we in a big company?
- Are we in a small company?
- Are we at start/mid/end of big/medium/small project?
- Are we at maintenance stage?

It could be a bad idea to introduce brand new framework at the late stage of a big project.
As well it might be an excellent idea just write the code as fast as possible with minimum side activities if you are a part of a small team at the small company.

Where are we going?
-------------------

How many times silence was the answer to this cursed question! The point of team's destination is paramount to the success of the project. You can't even measure the degree of success if you don't know what goal you need to achieve. Unfortunately, sometimes nobody can answer that question. Nobody at all. In such case, it might be useful to change this question to __What's the most efficient way to search for our goal?__

Most commonly you should ask yourself about closest milestones and release dates.

- Are we aiming for a major release?
- Are we going for a simple PoC?
- Are we going to show the demo to the stakeholders?
- Did we really commit delivering __that__ till Christmas?

If all you need to do is a basic internal demo for the team - there is no reason to invest time at documentation and CI for that.
And if you're going to publish new major update of your lib that will break half of old API - try to pay more attention to changelogs and comments in your code :)
Also if you're about to publish Android app to Google Play, it might be useful to try to launch it at some other than your device.

All of above mentioned seems quite obvious, right? What is the sense of writing this post at all? What is the profit?
And for me, profit starts when you combine all three questions together and start to act accordingly to the answers.

For instance, let's check next situations:

- You are a __small__ team at the __big__ company asked to __maintain__ old piece of code at currently __super-active__ service.

It's quite obvious that the best decision to make is just to maintain a piece of the code with minimum interference.
If you haven't first asked yourself 3 magical question, you could follow your instincts and start rewriting that ball of spaghetti you've received at once. And risk put the service to its knees in a blink of an eye.

On the other hand if

- You are a __big__ team at the __big__ company asked to __maintain__ old piece of code at currently __super-active__ service.

You can allocate some of your team-members to rewrite old code at the safe environment with proper QA. And gracefully update the current service.

Some more examples:

- You are a __small__ team at the __small__ company asked to __insanely fast develop__  a product to win __next investment round__ for your company.

You should really buy yourself a barrel of coffee and start writing code with little regards to how it smells. And how bad it actually is. The code quality won't matter at all if you don't deliver result fast enough to get the money.

Compare it with:

- You are a part of __startup__ that has already __gained__ some popularity. And now you're __competing__ with other companies for the __same user group__.

You still should be fast. But now you also should start to pay more attention to the quality and reliability of your product. You don't want to lose what you've gained because of sloppy update or security breach at your service. Now you should start looking for a balance in your team work.

I hope you can see how you can deduct what tools and approaches you should use depending on the situation you are in.

Responsibility and  Leadership
------------------------------

One little note - answering those questions requires some responsibility and leadership.  Sometimes you won't get the answers not because nobody knows them. But because nobody wants to be responsible for them. And since every question is a half of the answer - you might find yourself in a leadership role just by asking the questions.

Conclusion
----------

Software craft is a dynamic process of making hundreds of decisions under serious time constraints with a constant lack of information. So there are no silver bullet answers for all of the projects and teams. But there are correct answers for your project and your team. And to get the right answers, you need to ask correct questions.
