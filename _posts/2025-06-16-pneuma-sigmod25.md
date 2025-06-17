---
layout: post
title: "Pneuma: LLMs for Navigating Structure Data"
date: 2025-06-15 8:00:00
description: Overview of Pneuma, data discovery as a socio-technical problem
img:  # Add image post (optional)
tags: llm generative_ai pneuma rag tabular data socio-technical
---

Organizations are excited about LLMs for many reasons. A solution that helps organizations understand existing data would be a huge productivity boost, and more than enough to justify adopting the technology. And the current promise is to go beyond that and have the LLMs not only answer existing questions but also enable new ones.

To achieve that goal, we need ways to integrate organizational data into LLM-powered systems. Retrieval-Augmented Generation (RAG) is one popular approach. You've probably seen it in commercial models---ChatGPT searching the web is one example. But inside organizations, most of the most valuable data isn't in web pages or PDFs---it's structured, tucked away in databases or data lakes. So how do we build LLM systems that can *reason* over structured data?

We explore this question in the [Pneuma project](https://arxiv.org/pdf/2504.09207), which we'll present at SIGMOD 2025. If you're interested in the full details, [the paper](https://arxiv.org/pdf/2504.09207) is your best bet. And if you're ready to dive into the code, [here's the repo](https://github.com/TheDataStation/Pneuma)—feedback welcome!

This post provides a quick overview of a few core ideas that open up the design space in new ways and provides a brief update on what we’re doing next.

### **Let LLMs Work** Before **the Question Arrives**

In traditional RAG systems, the LLM only gets involved *after* a user submits a question. The query is used to retrieve relevant documents---often with a vector database---and the LLM then uses those documents to produce an answer. This approach hinges on retrieval quality: if the system retrieves irrelevant data, the LLM cannot magically provide the right answer.

Pneuma flips that around. Instead of waiting for a question, LLM agents preprocess the data—specifically structured tables—and generate natural-language summaries and explanations *before* any queries arrive. We call this output “context.” These summaries describe what the table represents and how it might be used, often including data samples to anchor the explanation.

When a user asks a question, the system retrieves both the relevant tables and their accompanying summaries. These summaries dramatically improve retrieval performance, and they let us represent an entire table with a single vector---far more efficient than representing every row individually. That means faster indexing, better retrieval accuracy, and a much smaller storage footprint.

### LLM as a Judge, Not an Oracle

Another idea in Pneuma: use a smaller, faster LLM not to *answer* questions, but to *evaluate* candidate answers. Specifically, we use this lightweight model as a “judge” that reviews the list of retrieved entries and filters out irrelevant ones.

This judge doesn't have to generate complex responses---it just decides whether each retrieved item seems potentially relevant. If not, it's banned from the results. What remains can then be passed to a larger model or a downstream application.

This strategy—giving easier tasks to smaller models—isn't new. But what's often difficult is avoiding a tradeoff between speed and accuracy. In this case, the task is so simple and the criteria so clear that the smaller model performs well with no quality compromise. It's a cheap and effective way to improve the overall system, and surprisingly easy to engineer into the ranking loop.

### **More Ideas in the Paper**

The paper goes further. We explain how to use LLMs to *automatically* generate benchmarks for tabular data and describe Pneuma's end-to-end architecture, which is significantly cleaner and more robust than our earlier system, Solo, which also tried to combine data discovery and RAG.

We also include plenty of experimental results showing where Pneuma improves on prior systems and how it compares to the state of the art. There's a lot that had to be done just right to get this system to work well, and the paper covers those design choices in depth.

### **What's Next?**

Pneuma expands the design space for RAG over structured data---but we're just getting started. Given the current pace of progress in RAG and agentic systems, and the increasing attention from researchers and industry, I suspect that the “retrieval” part of data discovery---i.e., how to get relevant data for a given need---will be *solved*[^1] relatively soon.

That shifts the bottleneck to a deeper challenge: helping users understand what they need in the first place. People come to these systems with very different levels of domain knowledge, background noise in their mental models, goals, and ability to articulate questions. How do we help users *figure out* what their actual information needs are?

[Belkin raised this question back in the 1980s](https://tefkos.comminfo.rutgers.edu/Courses/612/Articles/BelkinAnomolous.pdf), during the early days of information retrieval. We still don't have a great answer---today, we often rely on business analysts to interpret and translate those needs manually.

But there's room to do better. First, by recognizing that data discovery is a *socio-technical* problem, not just a technical one. And second, by using modern AI systems to help users refine and clarify their questions. That's the frontier we're exploring. Belkin's insight was ahead of its time, but with today's tools, we're in a much better position to do something about it.

[^1]: Of course, “solved” is relative. As technology improves, expectations rise, and the bar moves higher. But in this case, I mean we'll soon be able to tackle what currently feels hard---and doing so will unlock real value across many domains.