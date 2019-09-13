---
layout: template
title: Makeover Monday 2019/W37
sub_title: James Patterson Book Checkouts
---

# Makeover Monday 2019/W37 - James Patterson Book Checkouts

The dataset for this week was interesting, albeit a bit messy! It contained the records of checkouts of James Patterson books from the Seattle Public Library. The visualisation provided for the makeover, however, was not built on the same data, but on something very similar - Jane Austen novels and their popularity. Oh boy. I had to stare at that chart for many minutes before I actually understood what it was trying to tell me - but that might just be me.

![Image](https://media.data.world/25OkZFQ4a5dNOUmKwqLg_Screenshot%202019-09-07%20at%207.00.26%20pm.png)

## My thoughts on the visualisation:

### What works with this chart?

- It is **very visually appealing**, with a pleasant colour scheme that allows a more or less clear distinction between the different books/trends analysed.

### What doesn't work with this chart?

- Representing a change over time with **unconnected circles on a chart is very confusing**. It is not easy to follow the progression of each book and the result is that the viewer only gets a **general idea** of which volumes were more popular in a general timespan, but **any meaningful trend gets lost** in the mess;
- There is no clear scale for **what the size of the circles means**, as the y axis should already represent the volume of checkouts/web searches and there is no other legend in the chart;
- The **description of the y axis is confusing**, and it contains a word that is either a typo or a very outdated way of saying "volume" (volumn);
- Overall, it feels like whoever made the chart was **more focused** on making something that was **visually appealing** rather than on conveying accurate information or highlighting a particular trend.

### How can it be improved?

- Of course, the dataset we had did not contain exactly the same information contained in the Jane Austen visualisation, but the aim was the same: use the checkout records of the public library to show the change in popularity over time of the books from a certain author for the Seattle area. Therefore, I made the **area chart representing book checkouts over time the main piece of my dashboard**;
- Then, since many books from J. Patterson follow a series, I used a bar chart to show the viewer **which series were the most popular** by checkout numbers. I also allowed them to **filter the checkouts** over time chart to see only data relevant to a specific book series (or to books that do not belong to one);
- Also, seen how prolific an author J. Patterson is, I showed the viewer **how many books were published per year** (even if this might contain some **invalid data**, as sometimes the same book had more than one publishing year). This also allows the viewer to filter the checkouts over time/series charts by publishing data, revealing some trends on how checkouts tend to taper off in the years following the first publication;
- Finally, I added a small filter at the bottom to allow the viewer to **select a specific book** they might be curious about. This alters the other three charts, showing them if the book belongs to a series, when it was published, and how many times it was checked out during the years.

![Image](https://i.imgur.com/SEwSQfc.png)

[Interactive dashboard](https://public.tableau.com/profile/alepoptosis#!/vizhome/JamesPattersonBookCheckouts-MakeoverMonday2019W37/JamesPattersonBookCheckouts)

## How did I do it?

There is absolutely nothing special going on with this dashboard. I just used the two bottom charts as filters and added a visible title filter applied to all worksheets. It's the first week of my MSc, so pardon the simplicity! The only new thing that I learned is how to merge a year and month field to create a single date. It can be done with the `MAKEDATE(year, month, day)` function - in this case the calculated field looked like this:

`MAKEDATE([Checkout Year], [Checkout Month], 1)`

## Final thoughts

I had fun playing with this dataset, it was definitely interesting to see the spikes in book checkouts when a new volume was published and then see them taper off, and the differences between standalone books and series. As a book lover, it made me want to go out and look for similar datasets about my favourite authors! I wish I had more time/strength to clean the dataset before using it: the publisher names were all over the place, with the same publisher being present multiple times under slightly different names, and some books had multiple publication years, as I mentioned above. I am sure all that could have been easily fixed by spending some time with the file on python, but this wasn't the week for it. See you next time!