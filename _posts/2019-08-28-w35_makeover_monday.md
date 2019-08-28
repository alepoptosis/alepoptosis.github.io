---
layout: template
title: Makeover Monday 2019/W35
sub_title: PCs to become the smallest gaming platform in 2018
---

# Makeover Monday 2019/W35 - PCs to become the smallest gaming platform in 2018

This week's topic was very interesting to me personally, since I am a big fan of videogames of all kinds, and have been for years. The dataset was provided by [Statista])(https://www.statista.com/chart/13789/worldwide-video-game-revenue-forecast/), although I did some more digging and went straight to the source, i.e. [Newzoo](https://newzoo.com/insights/articles/global-games-market-reaches-137-9-billion-in-2018-mobile-games-take-half/) and their Global Games Market Report service, specifically the one from April of 2018. The visualisation to revamp is the one given by Statista, in which they show not only the overall increase in revenue that the gaming industry has seen since 2012, but also how the sector of mobile games has become more and more prominent when compared to PC and console games.

![Image](https://infographic.statista.com/normal/chartoftheday_13789_worldwide_video_game_revenue_forecast_n.jpg)

## My thoughts on the visualisation:

### What works with this chart?

- It is composed of a **single simple chart**, which helps the viewer stay focused on the main piece of information;
- The **colours are bright and easy to distinguish**, which helps comparison of the different sectors;
- The chart only contains **two essential sentences** to introduce the topic, keeping the visualisation as its centrepiece.

### What doesn't work with this chart?

- First and foremost, nowhere in the visualisation it is made clear that **data past 2017 is a prediction**, and not historical. This can be deduced by the title which hints at 2018 as being sometime in the future, but it should still be made as clear as possible; 
- The dataset provides both a total estimated revenue per sector, and what percentage of the total that value corresponds to. In this visualisation, they decided to use the **total estimated revenue** to build the bar, but since the values for PC and console change by very little, it is **difficult to detect smaller changes** that may have occurred over time;
- To compensate for this, the visualisation makes **heavy use of percentage labels** that can be seen on every single bar, resulting in the viewer having to manually compare each label to the one that follows for a more detailed view;
- Finally, the **labels at the top of each bar** that indicate the total revenue for that year, put there to compensate the removal of the y-axis, further contribute to the clutter of numbers on each bar. Every column, in the end, ends up **stacking 5 numbers on top of one another**.

### How can it be improved?

- At first I was a bit stumped, so I went to Twitter for some ideas and the piece that inspired me the most was [this one from @AshShih](https://twitter.com/AshShih/status/1165776133964492801). It pushed me to try a dark background for the first time, but more importantly it reminded me to indicate clearly that only the data from 2012 to 2017 is historical, while everything else is a forecast. To do this I **added a forecast line** in the first chart and an **introductory paragraph** under the title explaining it. I tried making the last four bars from the bar chart lighter to suggest a prediction, but I couldn't find colours that would work without cluttering the figure, so I just moved the bar chart after the line chart to ensure the viewer would already have that information by the time they get to it;
- I tried to solve the excessive labelling problem by using two charts, a **line chart** to indicate the **change in revenue of the different sectors over time**, and a **stacked bar chart** to show how the **mobile sector had become more and more prominent** when compared to the other two;
- Instead of using a legend, I decided to **integrate the colour coding not only in the charts themselves**, using labelled lines and columns, but also by **highlighting sections of the text** according to the legend;
- I added a **"Total" in the line chart** to be able to track the positive trend of the global gaming market, and to compare the growth of the entire industry to that of the mobile sector. I believe the similarity between those two lines says a lot about how much the mobile sector had to do with the growth of the last few years, especially when compared to the flatness of the console and PC lines;
- Finally, going against my choice from last week, I decided to **add a lot more descriptive text** than in the original visualisation. While I did like how uncluttered it was, I wanted to make the visualisation a standalone, capable of taking the viewer through the data and not just displaying it to them.

![Image](https://i.imgur.com/mVsotJR.png)

[Interactive dashboard](https://public.tableau.com/profile/alepoptosis#!/vizhome/PCstobecomethesmallestgamingplatformin2018-MakeoverMonday2019W35/PCstobecomethesmallestgamingplatformin2018)

## How did I do it?

I learned quite a few technical tips and tricks this week, which I'd like to share both for other newbies like me and for future reference:

1. I found out [labels can be moved freely](https://www.tableau.com/about/blog/2016/1/tableau-confessions-you-can-move-labels-wow-49277) around a chart. As straightforward as it seems, I just... never tried it!
2. I learned how to add a "Total" line to a line chart which shows separate groups: the trick is to create a dual axes chart which contains on one side the separated categories, and on the other the total without any distinctions. Find the tutorial [here](https://kb.tableau.com/articles/howto/line-graph-with-line-for-total-sum-of-other-lines). Just make sure that the two axes have the same scale before hiding one!
3. I practised more on formatting the entire workbook at once, since I had to recolour all the chart details to match the black background. However, for some reason which I still don't understand, the zero line of my line chart keeps disappearing in the published dashboard even if it is present when I work on it on my computer. The mystery of technology.
4. I thought it wasn't possible to extract an image/PDF from a workbook unless one is using Tableau Desktop, instead I learned that it is possible, simply once it is published on Tableau Public! Even though I had some problems, like the image cutting part of my dashboard for some reason, it is definitely going to be useful in the future.

## Final thoughts

I am quite happy with how this week's results look, even though the picture I posted on Twitter honestly does not do it justice (oh Twitter image compression, how do I hate thee). I ended up loving the black background and the different font (Consolas, which unfortunately does not show on mobile), even if it meant I spent more time on the colour palette than on the actual charts. I really want to hone my graphic design skills and learn how to use colours and shapes to better convey the information I am visualising - I might even have found a book to add to my reading list on this topic. Anyway, Makeover Monday has definitely become one of my favourite activities of the week, and I cannot wait for the next one!