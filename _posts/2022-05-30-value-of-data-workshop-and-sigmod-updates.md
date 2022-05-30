---
layout: post
title: "Three updates: value of data workshop and two SIGMOD papers"
date: 2022-05-30 17:20:00
description: Updates on workshop and sigmod papers 
img:  # Add image post (optional)
tags: value_of_data relational_embeddings data_markets
---

I want to share three updates. The first is about a workshop we are organizing on *the value of data* and that will take place **in just one week**, from June 6th to the 8th. The second is a summary/pitch of a couple of papers we are presenting at SIGMOD'22 in Philadelphia (12th to 17th of June).

###Workshop: [Data Value: Assessment and Evolution](https://www.imsi.institute/activities/data-value-assessment-and-evolution/)

With Professors Michael Franklin from UChicago and Jason Hartline from Northwestern, I've been organizing a 3-day workshop on the value of data ([check the schedule and invited speakers](https://www.imsi.institute/activities/data-value-assessment-and-evolution/)). This all started when [IMSI, the Institute for Mathematical and Statistical Innovation](https://www.imsi.institute/) at UChicago invited us to organize a workshop. I've found IMSI a great source of talks, workshops, and even longer courses on campus, and I encourage you to look at their webpage and see the breadth of topics they cover. 

Mike, Jason, and I put together a workshop program including researchers working on information economics, data management, operations research, optimization, machine learning, and many other areas. The workshop also includes a few sessions for students to present their work, and we will even have an industry panel to hear from companies building data markets and data market platforms. It looks pretty exciting.

One concrete goal I have for this workshop is to have a lot of discussion across the wide variety of backgrounds we are bringing together and produce some kind of report we can share widely afterward. I'd love for this report to summarize the things that we know, the things that we don't know but we want to know, the things that we don't know and that are likely not important (and why?), as well as a collection of ideas, reflections, and discussions we had. The good news is that if you are local (Chicago area), you can register and come. And if you are not local, IMSI offers some remote options: take a look and [register here](https://www.imsi.institute/activities/data-value-assessment-and-evolution/).

###SIGMOD22 Paper: [Protecting Data Markets from Strategic Participants](https://raulcastrofernandez.com/papers/protecting-data-markets-sigmod22.pdf)

This paper will be presented at [SIGMOD'22 in Philadelphia](https://2022.sigmod.org/index.shtml), which will be the first in-person conference I've been to since the beginning of the pandemic; I know this is true for many others. That alone is exciting. What makes it even more exciting is that some students are coming and this will be their first in-person conference *ever*.

Anyway, in this paper I do a few things:

- Present a data market model where data price is based on direct demand.
- Present a few protection techniques that help tame the strategic behavior that arises due to the explicit link between demand and price. And then introduce the results of a user study that: i) demonstrate the *types* of strategic behavior in the wild; ii) show the effectiveness of the protection techniques.

Let me write a paragraph on each of those:

Data is hard to price because you and I may use the same dataset for two very different things, yours being extremely valuable and mine extremely boring and useless. So how should the seller price the data? The average of your value and mine? Economics knows how to answer this question quite well for most assets. But data is unique as an asset. First, as I mentioned, it can be used for many different purposes. Second, nothing prevents you and me from using the dataset simultaneously because copying data is free and easy. Anyway, so the paper explains what I just said in a more nuanced way. Of all possible ways to move forward on the pricing problem, I chose one in this paper: *auction-type* mechanisms. Buyers express how much they value the data with bids. The market uses those bids (that represent the demand) to set a price for the dataset: i.e., the price of the dataset depends on the buyers' bids. Setting the price this way makes sense in principle as it achieves one important goal: the price of a dataset is a function of the dataset's demand. Yet, because bids are provided by humans (or humans will be in the loop in many cases), and humans want to get the best deal possible, we should not expect the bids they send to reflect their true valuation for those datasets. Instead, we should anticipate strategic behavior: humans developing strategies to get the data cheaply.

The bulk of the paper is the presentation of three protection techniques that a pricing algorithm can implement to avoid/ameliorate/tame the strategic behavior we should expect from the buyers interacting with the market. To come up with the techniques, I first wrote down a model and guessed what kind of strategic behavior would arise if I were to face this myself. I then designed a user study to check whether that was true. There were surprises. I was more or less on point with some of the predictions, but there was another kind of behavior I did not anticipate that was also harming the market. Won't get into details here, but it has to do with how (as evident as it sounds) actors are not as rational as the formal models suggest. So that was fun to figure out, and it was a great place to motivate the protection techniques themselves. Also, the user study was the basis of an extended one where we did evaluate the effectiveness of those protection techniques. All in all, this was quite a fun experience.

So what's the take-away message? One way of reading the paper is that there are ways of working around the difficulties of pricing data in a market such as the one we present (which seems easy to adapt to scenarios such as data augmentation for AutoML solutions, to complement today's data marketplaces, and many other use cases). Another way of reading the paper is that working around data's unique characteristics is hard and leads to perhaps too complicated solutions to be implemented in practice (notice I provide an algorithm in the market, but that's still many layers far from a real deployment).

I have thoughts for both interpretations, and the group is exploring a few of those. Looking forward to sharing them sometime soon! 

###SIGMOD22 Paper. [Leva: Boosting Machine Learning Performance with Relational Embedding Data Augmentation](https://raulcastrofernandez.com/papers/leva-sigmod22.pdf)

The bulk of this work was done by my student Alex Zhao, who started it as a 3rd-year undergraduate CS and stats major at UChicago and finished it in his 4th year, just before moving on to industry. Alex is great and all credit for the excellent results of the paper goes to him. He'll be presenting this work at SIGMOD'22 in Philly. 

This paper combines two of my interests: data discovery and relational embeddings. The goal is to boost the performance of supervised machine learning tasks such as classification and regression across various datasets.

This is the motivation. If you want to build a supervised machine learning model, you need a training dataset. The training dataset will have several features and a target variable, which is what you want to predict. What features are relevant to predicting the target variable? In general, you don't have a straight answer to this feature engineering question. Instead, you may use your intuition to guide the process (or rely on some higher capacity models such as neural networks doing feature engineering for you, if you can afford the tradeoffs). Still, there will be some back and forth while developing the model. Plus, even if you knew what features are relevant, you may not know where they are physically stored. They could be sprinkled throughout different databases. For example, if you want to predict a property of a new product for which you need both other products' data (which you can find in the product team's database) and data about marketing campaign's for those products, which you may only find by asking the marketing department data owner. 

This is the key idea of the paper. Build a relational embedding (a vector representation of relational data) that represents all tables that may contain any feature that could be helpful for any potential target variable you consider. The embedding will be quite inexact, in that to build it you will have to guess what tables join with each other (I say *guess* because it is impossible to identify precise *joins* automatically). The imprecision introduced by guessing joins across tables, however, is compensated by the existence of a supervision signal downstream, which will help morph the original relational embedding into a representation much more amenable to the downstream task.

In practice, Leva, the system Alex built works as follows. First, you point to a bunch of tables you think may contain relevant features. Leva produces an embedding. Then, before feeding your training data to the ML model, you use the embedding to *featurize* your training data. Because the embedding contains a distributed representation of other (related) information from the rest of the tables, if any of that information is useful for the training task, it'll come out during training, and the result is that the final model will perform better. 

I like this paper a lot because it's a clear example of how much one can gain in ML by just focusing on the data! I started working on relational embeddings with Sam Madden at MIT, where we wrote down some ideas in a workshop paper, [Termite](https://arxiv.org/abs/1903.05008). Since then, there has been a lot of work -- I highlight Paolo Papotti's [EmbDI](https://arxiv.org/abs/1909.01120), for example. I see Leva as an application of what we've learned so far to a new exciting problem. There's a lot of excitement in this area and a lot more relevant work coming soon. 

