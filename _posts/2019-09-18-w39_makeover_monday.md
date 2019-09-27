---
layout: template
title: Makeover Monday 2019/W39
sub_title: The reasons behind eviction
---

# Makeover Monday 2019/W39 - The reasons behind eviction

This week's data investigated the important issue of evictions in the city of San Francisco, in California. As the area has become more and more of a hub for tech companies, it has been more difficult for people of lower income levels to stay in their rented homes, as landlords try to make their properties appealing to the higher income workforce that those companies attract. The dataset contained data on evictions carried out from 1997 to 2019, and included the when, where and why of each eviction notice. Here is the visualisation given to the community for improvement, highlighting the number of evictions for the top 10 neighbourhoods over time:

![Image](https://greenet09.github.io/datasophy/2018/08/08/sfevictions_files/figure-markdown_github/unnamed-chunk-3-1.png)

## My thoughts on the visualisation:

### What works with this chart?

- The **question** this visualisation asks is **very interesting**: have different neighbourhoods been affected by evictions in different ways over the years? And the answer is very clearly yes, as it is possible to see how the Castro/Upper Market area is consistently much more affected than others, with only three instances in which dramatic peaks in Lakeshore and South of Market surpass it.

### What doesn't work with this chart?

- When trying to identify the neighbourhoods that presented those three peaks in the section above, I had to turn up the brightness on my laptop to the maximum, squint, and get very close to the screen in order to identify the correct colour match from the legend. In other words, the colours are **too similar to each other** and the **lines are too thin** to quickly distinguish which neighbourhood is represented by which line;
- While we identified the most affected neighbourhood and three outliers relatively quickly, the **bottom of the graph looks more like tangled yarn** than actual data. It is almost impossible to distinguish any trend, and after a quick glance the viewer is bound to just dismiss it in favour of the little information that actually transpires. 

### How can it be improved?

Before I get into what I made, it is necessary to give yet another shout-out to Andy Kriebel, a.k.a. [@VizWizBI](https://twitter.com/VizWizBI) for the inspiration that he give me and I am sure many other participants with his [livestream](https://www.youtube.com/watch?v=iDhNdbaUgHk) on Monday. It was clear when the favourites came out that his approach was well received, and that we all learned a lot from watching him work.

Personally, I decided to adopt a similar approach to his, and focus on the questions when?, where?, and why? 

- The *when* was the easiest, I simply produced a bar chart which looked at the number of evictions per month from the beginning of 1998 to the end of 2018, given that the data for 1997 and 2019 was incomplete. The month-by-month approach allows to spot trends over the years, for example a decrease in evictions around December (basic decency, one would hope).
- The *why* was also very straightforward, with a bar chart showing the top reasons for eviction. Personally, I like to keep the "other" category at the end, which is why the bottom bar is not the smallest, even though the other categories are indeed ordered by number of records.
- The *where* was by far the most fun and interesting, as I used a hexbin map to display the areas where evictions hit the hardest (see next section to learn how to build one). However, due to a few data points with an unusually high number of records (the three peaks shown in the original vis), the range is too wide to actually show regional differences. It is useful to select an area for filtering, however.

Last, but not least, I allowed the viewer to use any graph to filter the others, because a Tableau dashboard would not be a Tableau dashboard without at least one "apply to all" filter. I believe, through these three graphs and the filtering ability, that the viewer is now able to have a better overall understanding of the dynamics behind eviction.

![Image](https://i.imgur.com/RGGQs91.png)

[Interactive dashboard](https://public.tableau.com/profile/alepoptosis#!/vizhome/Thereasonsbehindeviction-MakeoverMonday2019w39/Thereasonsbehindeviction)

## How did I do it?

While the first two charts are quite straightforward - two bar charts, really doesn't get any more better than that - the hexbin map was fun to learn and fun to build. I learned how to make it just this week through Andy's livestream, since even though I had seen them a few times in visualisations, I had never asked myself how they had been made. 

These maps are based on rounded-off version of geographical coordinates, and they are useful for representing geographical areas without having to generalise by country or state, but also without having to treat each separate coordinate set as its own data point, which is often way too crowded. If you want to learn how to make a density map/hexbin map, either have a look at [this simple tutorial](https://www.tableau.com/about/blog/2016/7/how-create-density-maps-using-hexbins-tableau-56511) I found on the subject, or have watch from [minute 19 of Andy's livestream](https://youtu.be/iDhNdbaUgHk?t=1140).

The only thing I am a bit annoyed about with this solution is that, since the coordinates are rounded off, I could not add the neighbourhood each area belonged to in the tooltip, as some areas belonged to more than one and I could not find a way to properly show all values in the tooltip instead of that dreaded "\*". Now that I type this though, I am thinking I maybe could add a neighbourhood filter, either as a filter on its own or as a graph... These visualisations are never really done, are they!?

## Final thoughts

This week, I tried to take it easy, between the stress from last week's vis and the fact I have been ill since last Friday now. So, when it came to designing this vis, I kept it simple: monochromatic, white background, basic overview of the data with classic modes of representation. I did not expect it to generate attention, and yet it was picked as a weekly favourite - and this is not the first time this happens! I guess this only taught me again that less is more, and that clarity trumps all. But most importantly... I can't wait for more geographical data to make more density maps!

