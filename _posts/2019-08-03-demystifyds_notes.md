---
layout: template
title: DemystifyDS conference, day 1 highlights
sub_title: My personal notes from the first day of the Demystify Data Science conference
---

# DemystifyDS conference, day 1 highlights

The [Demystifying Data Science](https://www.thisismetis.com/demystifying-data-science) conference is an annual free online conference hosted by [Metis](https://www.thisismetis.com/), a company that provides data science training for companies, individuals and institutions. 
As someone who has only very recently found their love for data science, I registered as soon as I found out about the event on Twitter, and seen as not everyone might have been able to follow the live event (often due to pesky jobs and time zones), I decided to collect the notes I took from the 8 amazing speakers that dropped tons of knowledge on all of us on Day 1. If you find this interesting, make sure to follow the speakers on Twitter, as well as myself at [@alepoptosis](https://twitter.com/alepoptosis).

---

## From Aspiring to Full-fledged Data Science Professional
### Tarry Singh - [@tarrysingh](https://twitter.com/tarrysingh)

> "Don't try to boil the ocean."

Tarry spoke about the different levels of data science that lead to the industrial applications of AI as 5 plateaus, which need to be climbed progressively. These plateaus are:

**1. Fundamentals of data science**: statistics, probability, mathematics, computer programming. These are to be regularly revisited and refreshed, especially those that are relevant to the applications one is directly invested in at the time.

**2. Data visualisation tools**: these are technologies like Tableau, the matplotlib and seaborn packages for Python, ggplot for R and so on. He suggested to learn these tools when relevant for the project at hand, and to focus one's energy on one of these at a time, to really understand it, instead of only having a vague knowledge of all of them.

**3. Machine learning**: supervised and unsupervised machine learning tasks and their relevant algorithms. Again, Tarry stressed the importance of not spreading oneself too thin, and that the most important thing is to make sure one is able to understand the data of the project at hand. Someone who reaches this plateau should already consider themselves a data scientist.

**4. Deep learning**

**5. Applied AI**

The point I think Tarry tried to get across - as well as many other speakers - is that nobody is ever going to be an expert in everything, therefore the most important thing is to have a good grasp of the fundamentals and be ready to dive into new tools and technologies when needed.

---

## Qualities of an Exceptional Data Science Team
### Kate Strachnyi - [@StoryByData](https://twitter.com/StoryByData)

Kate listed a very interesting series of skills that would make an excellent data scientist, or data science team. I found these particularly interesting, as people (including me) are often at a loss when trying to think of skills to showcase in their CV, especially so-called "soft skills". I transcribed the entire list here for future reference.

**Business/Domain knowledge:**

- Understanding the common issues of the industry
- Balancing accuracy and timely results
- Understanding the common constraints of the company/industry
- Familiarity with the specific language of the industry

**Technical skills:**

- Statistics, mathematics, probability and linear algebra
- Computer programming
- Data collection and storage
- Database management
- SQL/Querying
- Data cleaning, exploration and wrangling (what a data scientist spends most of their time doing)
- Data integrity and reproducibility (i.e. making sure someone else can repeat the same process and obtain the same results, documentation is critical to this)
- Machine Learning algorithms
- Data visualisation

**Soft skills:**

- Communication and data storytelling
- Passion for problem solving and puzzles
- Curiosity, patience and perseverance
- Good project management, including budgeting, staffing and planning a timescale
- Creativity, good design skills
- Being proactive, taking initiative
- Collaborative, both with colleagues and online communities
- Critical thinking, intuition
- Ethical use of data

Apart from this list of skills, Kate also mentioned a very interesting initiative called [Makeover Monday](http://makeovermonday.co.uk/), which provides the community with a new dataset every week, inviting people to produce beautiful and informative ways to visualise that data. I certainly will do my best to participate whenever I can now!

---

## Structured Thinking and Communication for Data Scientists
### Kunal Jain - [@jainkunal](https://twitter.com/jainkunal)

Kunal presented the idea of **structured thinking**, i.e. bringing a framework to an unstructured problem. Data scientists are usually required to do so with complex problems, in an hopefully unbiased way, and sometimes with little experience - which is why Kunal suggests using structured thinking. He indicates that, especially, it should be used every time one does something new, something big, or something which has a very high cost of failure.
He introduced an acronym he uses to turn a business problem into a data problem: TOSCAR. He indicates it as a technique to create a **problem statement**, which is something that should be defined before touching any data.

**TOSCAR:**

- **Trouble**: identify what is the problem, why is that a problem, why is it a problem now;
- **Owner**: identify as exactly as possible whose problem it is;
- **Success criteria**: define what does success look like;
- **Constraints**: identify possible constraints in budget or communication;
- **Actors**: identify stakeholders and their interests;
- **References**: find past attempts at solving the problem and what they resulted in.

Kunal also gave two book suggestions:
- [The McKinsey Way](https://www.goodreads.com/book/show/206260.The_McKinsey_Way), by Ethan M. Rasiel
- [The Pyramid Principle](https://www.goodreads.com/book/show/3981669-the-pyramid-principle), by Barbara Minto

---

## How Charts Lie - Getting Smarter about Data Visualization
### Alberto Cairos - [@albertocairo](https://twitter.com/albertocairo)

> "Show AND tell!"

Debunking statements such as "Show, don't tell", and "A picture is worth a thousand words", Alberto talked about how **data visualisation can be ambiguous**, even if many think it is inherently intuitive to human beings. 

He sees the problem as a **lack of shared mental models**, i.e. the way the creator of a visual interpreted the data behind it and expects it to be understood does not often match the way the viewer does.

This is not only something that applies to people that are new to data visualisation. Alberto talked about how, when seeing a visualisation, everyone creates a **mental descriptions** of it in their head. He finds that it is very easy to create a wrong one, at all levels of expertise, and recommended to always double check before drawing any conclusion. 

For these reason, Alberto suggested testing our own visualisations with **non-experts**, trying not to bias them in the process, to make sure they can be easily accessed by anyone. When this is not the case, he believes it is important to make sure to **explain the logic behind a graphic** with as much text or words as one needs, without fear of sounding redundant.

Finally, he encouraged creators always try their best to balance **oversimplification** and **overcomplication** in their visualisations.

Apart from his upcoming book, [How Charts Lie](https://www.goodreads.com/book/show/43726576-how-charts-lie), Alberto also recommended that listeners check out the work of Hans Rosling, especially when it comes to his way of presenting visualisations, as well as his book [Factfulness](https://www.goodreads.com/book/show/34890015-factfulness). Personally, I just started watching his talks, and it just made me even more eager to work on my storytelling skills.

---

## Deep Learning for All
### Gabriela de Queiroz - [@gdequeiroz](https://twitter.com/gdequeiroz)

Gabriela presented useful asset packs for Deep Learning:
- [Model Asset Exchange](https://developer.ibm.com/exchanges/models/), or MAX: free, open source deep learning models, with a choice of trainable and deployable models. The MAX also comes with its own set of [tutorials](https://developer.ibm.com/series/create-model-asset-exchange/).
- [Data Asset Exchange](https://developer.ibm.com/exchanges/data/), or DAX: free, open source datasets

Gabriela's talk highlighted how the idea of **creating and deploying** a model is sometimes seen as easier than what it actually is. She outlined the necessary steps that precede the actual application of a deep learning model:

1. Find model: this needs to not only do what one needs, but also be free to use and perform well;
2. Find the code for the model: finding a good implementation of the code is not always easy;
3. Verify the model: check that the model meets all the above criteria;
4. Train model
5. Deploy model
6. Use model
7. Profit! (hopefully)

Gabriela also brought attention to the [AI inclusivity project](https://www.ai-inclusive.org/), which aims at increasing the representation and participation of gender minority groups to AI through education and mentorship. The project is still starting up, but I followed them at [@AIinclusive](https://twitter.com/AIinclusive) to stay in the loop once they get going.

---

## Joining the Data Science Community
### Emily Robinson - [@robinson_es](https://twitter.com/robinson\_es)

> "You'll never be an expert in all of data science!"

Emily's talk was the one I was looking forward to the most, seen as I am so new to this world and would love to form a network of data scientists I can interact with and look up to. She asked, first of all, **why is it important to network?"**

- To build connections;
- To gain opportunities;
- To start a snowball effect;
- To give back to other people in the community.

Here are some of her tips for starting a network, and for doing so effectively:

- Attend **local meet-ups**, or find online events if you live in a remote area;
- When talking in a group at an event, use the **Pacman rule**: leave always an open spot for someone to join the conversation;
- **Twitter**: 
	- Ask the community for help using the most common hashtags,
	- When attending conferences, live tweet the talks, take pictures, use the relevant hashtag, and tag the speakers,
	- Share yours and other people's work, and tag them when doing so if possible;
- Keep some artifacts of **public work** (GitHub, blog etc.). This not only will show others what you can do, but will also help against Impostor Syndrome (this part of the talk is where the initial quote comes from, which I honestly find extremely reassuring);
- **Start networking early**, not only when you need to (e.g. when looking for a job).

Emily and Jacqueline, the last speaker, have written a book together called [Build Your Career in Data Science](https://www.manning.com/books/build-your-career-in-data-science?a_aid=buildcareer&a_bid=76784b6a).

---

## Tech Won’t Save Us: Reimagining Digital Information for the Public
### Safiya Noble, Ph.D. - [@safiyanoble](https://twitter.com/safiyanoble)

Safiya presented the problem of **bias in search algorithms**, bringing important real-life cases in which Google searches have perpetuated racist terms and beliefs. Search engines should not be thought of as neutral filters, as they can reflect the bias of users and search results (like in the case of a fake news article showing up at the time of the results of the 2016 American election), or even be directly tampered with.

Safiya suggested what could be done to improve the situation:
- Demand healthy, factual, socially just information;
- Require digital literacy of policymakers;
- Fund critical digital media research, literacy programs and education;
- Create multiple paths to knowledge, and curate the indexable web;
- Reduce the over-development of technology, and thus its impact on people and on the planet;
- Engage the humanities and social sciences as much as the information and data sciences.

Safiya wrote a book called [Algorithms of Oppression](https://www.goodreads.com/en/book/show/34762552) which delves deeper into the topic of search engine bias.

---

## You’re Not Paid to Model
### Jacqueline Nolis - [@skyetetra](https://twitter.com/skyetetra)

Jacqueline's talk was dedicated to **debunking the myth** that most of what a data scientist does has to do with **building machine learning models**. In reality, that only makes up about a 33% of the total work, while the remaining 67% is spent

- Getting the data from different departments,
- Cleaning the data,
- Carrying out feature engineering,
- Testing the accuracy, usefulness and reproducibility of the results,
- Creating work reports,
- Presenting the data.

Most importantly, Jacqueline specified how it is a lot more important to **keep a project going** than to get stuck on a complex model that ends up taking most of the analyst's time, and eventually ends up killing the project itself. It's better to settle on a system that is quicker to set up and maintain, in order to have time to focus on the more important parts of the project.

She also stressed the importance of **communicating regularly (every 3-5 days)** with the project stakeholders in order to keep them in the loop, especially in case the project is taking longer than expected.

--- 

I hope these notes helped you figure out what you missed out on, or refresh what you already heard. Overall, I loved attending the conference! The speakers were friendly and approachable, I deeply appreciated the great diversity among speakers, and I always felt welcome and involved. I can't wait for the next opportunity to discover more about this community and the inspiring people in it.
