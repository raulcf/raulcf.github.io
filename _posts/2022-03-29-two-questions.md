---
layout: post
title: "Two broad questions"
date: 2022-09-29 19:41:00
description: Two broad questions
img:  # Add image post (optional)
tags: data_markets economics_of_data value_of_data research
---

In the previous post, I [summarized how during my first two years at UChicago](http://raulcastrofernandez.com/init-post/), my group has been thinking about *what is the value of data*. In this post, I want to follow up with a few more details about the projects and problems we are exploring:

There are two key high-level questions that drive ~90% of the research in my group these days:

- *What is the value of data?*
- *How do we distribute the value of data?*

The bulk of the work is really concentrated in the second question, but we cannot (shouldn't?) distribute the value of data if we do not know what that is.

###### What is the value of data?

Good data can help us make better decisions. This simple statement is at the core of [information economics](https://en.wikipedia.org/wiki/Information_economics#Value_of_information) and decision theory since, at least, this paper from Ronald Howard in [the 60s](https://ieeexplore.ieee.org/document/4082064). Before using a dataset to inform a decision, this dataset has had a long life: from data collection to preparation, to understanding, and more. Managing data helps us distill what datasets are really valuable for the task at hand and which ones are a distraction.

I haven't defined what "value" means, and it means many different things: the whole point of asking this question is to tease those apart and see which ones are actionable or at least help us make sense of an otherwise complex ecosystem of tools, buzzwords, etc. In more detail, there are many definitions of value that depend on context, task, and the person who is conducting that task. Multiple communities of researchers (in economics, computer science, electrical engineering, and more) and practitioners (traders, accountants, consultants, analysts) have thought about this question many times before. Our most immediate goal is to come up with definitions of the value of data that we can use to design algorithms and systems to do better data management.

###### How do we distribute the value of data?

An even bigger emphasis of the group these days is on envisioning ways of distributing the value of data. Doing so requires technical and social mechanisms---it is as much a technical as a "human" challenge. To tackle the technical challenges, we are building new systems to share, discover, integrate, process, and manage data. And to tackle the social (think incentives, privacy, regulation, compliance) aspect, we are designing different data markets. When I say market, it is natural to think about "money". But these are not the only markets we are studying. When you give your data away to Meta, Google, or Netflix in exchange for the service they provide, that is a data market. A well-designed data market would encourage data producers to document and prepare their data for consumption. Data markets can help incentivize the formation of data-sharing consortia, so organizations in the same sector can pool their data together, for example. We have a market design for each of the examples above and a few more. So by market, just think of a "distributed algorithm", how do you set up rules that when followed by the participants you get to a desirable outcome. Taken that way, it sounds a lot like [mechanism design](https://en.wikipedia.org/wiki/Mechanism_design), and surely we've been learning a lot about that! But we are also studying alternative ways of understanding how to design these markets, in different scenarios, so that every participant benefits from accessing data.

What I find really exciting is the connection between these market designs and the system infrastructure required to support them in practice. There are lots of challenges at this intersection which I think will keep us busy for a while. We don't have clear answers to those challenges yet, but we have learned a lot and keep making good progress. There are a couple of concrete next steps I plan to explain in the blog. The first is a framework to think about the "value of data". I'm using this framework to write a survey: the framework is more valuable as an artifact to convey a huge body of literature than as a concrete actionable instrument, but we need to start somewhere! The second is a more in-depth list of the kinds of data markets we are studying. More soon.
