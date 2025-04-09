---
layout: post
title: "Human- or Machine-Generated? Identity as a Double-Edged Sword"
date: 2025-04-08 6:00:00
description: Thoughts on content generation, privacy, identity, provenance
img:  # Add image post (optional)
tags: privacy ecology human-machine


---

Distinguishing humans from machines online will soon become nearly impossible. Even today, **separating human-generated from machine-generated content is difficult**, and the *gap* is rapidly growing. While this blurring has potential benefits, it also poses serious risks---cybercrime, mass manipulation, and, at worst, the erosion of social norms that hold society together. **This post argues that there is a class of technologies that can address this problem**. However, **deploying these solutions within the current ecosystem introduces new risks**, particularly the misuse of human-generated data, with consequences **far worse than the privacy violations of the past two decades**. To move forward, we need a more holistic view of our data ecosystems[^1] and a deeper understanding of the impact of **strong identity technologies**.

**The problem**

Let me illustrate the problem with a recent experience. As a professor, I regularly talk to students, peer researchers, and data experts from various organizations. A few weeks ago, I spoke with a soon-to-graduate student applying for jobs who wanted my advice. Later that day, I met with a senior software manager at a large company.

The student mentioned using an LLM to turn their CV into a narrative—an essay showcasing their abilities and aptitudes in what they believed was a well-articulated, industry-aligned way. Meanwhile, the senior manager described how their company was experimenting with LLMs to streamline hiring. While they weren’t outright rejecting applications based on LLM-generated classifications, the technology helped categorize them, reducing the manual review effort. What caught my attention was their claim that the most valuable use of LLMs in hiring was summarizing applicants' long, narrative-driven essays into concise bullet points.

In other words, applicants were using LLMs to expand their text, while companies were using LLMs to condense it back down. This is absurd but not necessarily dangerous. However, it illustrates the quality and capacity of LLMs to manipulate text in a way that fuels day-to-day business processes as important as hiring. It reflects a broader force that, unlike this hiring loop, could reshape society in far more profound ways. For example, **if decision-makers work with mostly machine-generated content, they may lose track of the original material**. Information overload will only grow to the point where there is so much of it that our only chance of going through it is ignoring everything---with significant repercussions for how societies work. Last, **the predominant narratives for certain issues may be machine-generated: this does not need to be bad, but it can be disastrous**. 

The example above highlights how easily content can be produced and consumed. I have no reason to believe the essay exchanged between the applicant and the hiring manager was fraudulent---it was likely based on real accomplishments. But **in a world where machines play intermediary, misleading and fraudulent content will be harder to identify**. Distinguishing between genuine and artificially generated content is becoming increasingly difficult. In fact, the content doesn't even need to be created by a human. The current use of LLMs in information operations (creating and coordinating the dissemination of misinformation) already demonstrates this, and we’re only at the beginning.

Consider the online interactions we take for granted---chatting, engaging with customer support, reading the news, or responding to emails. In all these cases, we assume a human is on the other side, whether assisting customers, reporting news, or writing messages. However, as generative AI becomes ubiquitous, this assumption will no longer hold.

To be clear, I am not claiming that non-human-generated content is inherently bad. The problem is that **when we can no longer tell whether a human or a machine created something, society as we know it will change**---and I have no reason to believe that change will be for the better; shouldn't we at least have a say? or, at the very least, control its effects? A reasonable path forward is to anticipate and respond to these shifts in a balanced way---maintaining accountability where needed and minimizing potential harm.

**The solution**

**As machine-generated content becomes dominant, the ability to distinguish it from human-created content will become increasingly valuable**. A strong **market demand for this distinction will drive the development of new solutions**. Two key elements will be essential to future solutions: i) *a robust concept of identity*; and ii) *a renewed social contract*. I will explore both next.

In the future, whenever we interact with an online system, we will want to know whether we are engaging with a human, a machine, or a mix of both. The challenge lies in identifying not just the creator of the content but also any other entities that shaped it. **The strongest form of identity is provenance**---the ability to trace an object's origins and the transformations it underwent before reaching us.

For example, if we encounter an online document, its provenance could reveal whether its data was collected by a human or generated by an LLM for a simulation. If we interact with a model, its provenance could detail the data used for training and how it was sourced. **Provenance, as a form of identity, offers a solution to distinguishing human from machine**.

But **for provenance to be effective**, we need more than just technological changes. We also **need a shift in our social contract**: we (i.e., humans) must demand provenance. If you create content based on news, your content should cite its sources, which themselves should come with provenance. If provenance becomes the norm, content lacking it will immediately raise suspicion. To put it bluntly: **we will have to teach kids to disregard content without provenance just as we teach them not to take candy from strangers**.

Building provenance into our systems presents many challenges. These have been widely discussed, with various proposed or theorized solutions. While the technical difficulties are fascinating and warrant further research, they are not the focus of this article. Instead, I assume that some form of identity---whether a strong identity based on provenance, as I have argued, web3, or a yet-to-emerge technology---will develop in response to market demand for distinguishing humans from machines.

Now, **I will argue that if these technologies emerge before we have resolved our current relationship with data and data ecosystems, they will create chaos**.

**The challenge the solution brings**

The concept of privacy is old, but it began evolving rapidly in modern times, particularly after Warren and Brandeis’s famous article. In the post-WWW information era, privacy has become tied to the digital traces people leave online, the data brokers who aggregate and profit from that data, and the platform infrastructures that enable this market by collecting and repurposing user data.

Privacy violations are undesirable, but they are not the worst consequences of data misuse. Surveillance capitalism is one theory of how many of our data ecosystems are evolving in ways that harm individual users. The risks go beyond mere privacy violations: as data collection intensifies, so do concerns about its use in law enforcement, insurance discrimination, and other forms of decision-making that can negatively impact people's lives. These harms will only grow as our digital footprints expand and our ability to mine and exploit them improves.

Despite the ominous picture above, **today, only a handful of highly capable organizations can aggregate data at scale in a meaningful way**---which may or may not be a reason to breathe easier. Thanks to a patchwork of privacy regulations and shifting social pressures, **most organizations do not openly share customers’ unique identifiers in the wild**. For example, in the U.S., sharing Social Security numbers---the closest thing to a universal ID in this country---is legally restricted and rarely done. In Europe, GDPR and a decade of regulatory leadership have curbed the open exchange of personally identifiable data. In summary, the barrier of entry is high, limiting such data sharing to a few companies.

Such barriers will collapse once strong identity solutions are readily available. **A world with strong identity solutions and, simultaneously, private data hubs[^2] that do not owe accountability to anyone is the worst possible in terms of the potential harm such data may inflict on the individual from where the data stems in the first place**. This is because any organization will be able to mine and exploit such data to its benefit, which, in many cases, will correspond to a negative impact on individuals, well beyond privacy violations. It is for this reason that we are at a critical inflection point. **We need identity solutions to tell humans from machines. But these technologies need to be deployed in a data ecosystem that removes power from data hubs**. Failing to fix the data ecosystem first won’t just preserve today’s problems---it will make them exponentially worse.

**What can we do**

**Fortunately, much can be done**---and many are already tackling this challenge. Yes, we must invest in future identity technologies to distinguish humans from machines and ensure society continues collaborating toward growth, innovation, and shared prosperity. But **before these technologies can take root, we must confront the overuse of data head-on**. Acknowledging that **much of the value large online companies derive comes from vast, privately held data troves, we should consider managing such data as a collective resource[^3] rather than leaving it concentrated in private hands**. This would prevent data from being used for arbitrary purposes, which is what happens today and what would become worse if in addition to data we had full provenance on how that data came to be[^4]. 

**We tend to take our data ecosystem for granted**. Companies come and go, offering products we adopt, exchanging bits of data along the way, all while continuing our routines---streaming music, visiting doctors, grocery shopping online---**aware but often uncritical of data’s expanding influence** over these interactions. Yet, **this influence is not dictated by some unstoppable force; our collective choices shape it**. And that is good news---it means we have the power to change it. Recognizing the problem is the first step; acting on it is the next. We already have the tools to reshape data ecosystems to support the strong identity solutions our future demands. There has never been a more exciting time to be engaged in data research: reach out if you want to chat more about this.

[^1]: For a high-level [1-page overview](http://raulcastrofernandez.com/ecology.html) of data ecology -- how we are studying data ecosystems, take a look at this page. Also, take a look at our research initiative here and sign up for the newsletter if this is really interesting to you as we'll be sharing content there very soon.
[^2]: I use data hub as an umbrella term that includes data brokers and online platforms that, while ostensibly existing to provide a service such as search, content recommendations, and retail, are in effect a collection of data.
[^3]: many will see political links in this statement. In practice, we can govern data in much the same way we govern other shared resources such as lakes, rivers, and in the same way we (ought to) take care of the atmosphere and so on. Collectively managing data does not need to be tied to a specific political system.
[^4]: As a plus, a data pool governed by the collective set of people who generated it would permit those people to train a plethora of LLMs they could jointly benefit from.
