---
layout: post
title: "On value, cost, and how to save money when running SQL Queries on the Cloud"
date: 2024-08-24 8:00:00
description: Overview of Arachne
img:  # Add image post (optional)
tags: redshift bigquery arachne vldb24


---

What is the value of data? How can we harness data's value? I am obsessed with these questions. We (my research group) spend a lot of time looking into improving data ecosystems so *agents* benefit more from data (this is the premise of data ecology). We also spend a lot of time designing and developing systems (technical interventions, in the terminology of data ecology) to make it easier for people to control how they share and thus extract value from their data.

An important aspect that I haven't talked much about yet is **cost**. Briefly (and abstractly), say you have tasks that are valuable to you when completed; here's one way of thinking about data's utility. First, data's (instrumental) value is the extent to which access to data helps you solve those valuable tasks. While using data to complete the task, you incur some costs. These costs include sourcing and preparing the data and, crucially, *the costs of using the tools needed for the job*. Let's make this more concrete with a simple example. Consider you are making a decision worth $100K and use data to inform such a decision. Data is valuable because you are less likely to make a good decision without it; think of data as guiding you in the right direction. To leverage data to solve this task, you also incur costs such as the cost of the engineer preparing the data and **the cost of running queries in the cloud**... it gets complicated quickly, and I want to emphasize this example is an oversimplification of the process. I am preparing a paper that fleshes this out in more detail. But before that is out, I want to concentrate on the bolded text above because this is one of the key concerns that [Arachne, a system that my student Tapan Srivastava has created to address this problem](http://raulcastrofernandez.com/papers/arachne-vldb24.pdf).

Cost takes many forms: effort, time, money... Arachne deals with the monetary ($$$) cost of running workloads in the cloud. Let me briefly explain the main insight the paper exploits.

### Running SQL Workloads in the Cloud is expensive.

Before the cloud, to compute the cost of a query, you'd have to do something like this: track the costs of hardware, database system, and associated maintenance costs. Then, identify how many queries the system helped you serve throughout its life so that you can compute an approximate "monetary-cost-per-query". This would give you an approximate glimpse of the cost (there are other sources of cost involved; my intention is not to be exhaustive but to build some intuition). What is more important about this scenario is that you would pay for resources upfront and don't need to think about individual query costs.

With the cloud is different. You pay for what you use. This essentially means that cost optimization becomes an important concern. We care not only about databases that run queries fast but also about systems that run queries *cheaply*. Latency matters, but it matters more for some queries than for others. For example, it is common for many organizations to run nightly workloads. These queries are submitted at the end of the day and produce results that are only consumed the next morning. If the results are available at 3 am versus 8 am, there is little marginal utility impact for the consumers, e.g., because they arrive at the office at 9 am anyway. But what if we could pay much less to run those queries (i.e., if we could reduce the cost) by using those additional 5 hours? This is the question Arachne explores.

### Schedule Queries Across Cloud Databases with Different Pricing Models

The key insight is that cloud vendors use different pricing models to charge users for their queries and that some queries are naturally cheaper to run in one model than the other. Some pricing models charge you according to the time used to run the query; we call these *pay-per-compute* pricing models. Others charge you according to the amount of data that query reads, *pay-per-byte*. The first pricing model does not care about how much data your queries read, and the latter does not care how long it takes for the query to run. This opens up the possibility of judiciously choosing where to run queries (and sub-query plans, that is, pieces of a query) to save money.

[Arachne is the name of the system Tapan built to exploit this insight](http://raulcastrofernandez.com/papers/arachne-vldb24.pdf). It incorporates a couple of different strategies to save money. He has evaluated it on cloud vendors' data systems such as AWS Redshift (mostly a pay-per-compute system) and Google's Big Query (mostly a pay-per-byte system). The results are pretty interesting, with savings of up to 60% in some cases, which becomes significant when you realize many workloads are not latency-sensitive.

The [paper](http://raulcastrofernandez.com/papers/arachne-vldb24.pdf) will be presented at VLDB this week. Take a look and send us any feedback or questions you have.
