---
layout: template
title: Makeover Monday 2019/W32
sub_title: Britain is rapidly phasing out coal
---

# Makeover Monday 2019/W32 - Britain is rapidly phasing out coal

The data provided for this week's Makeover Monday was from Gridwatch, and it contained the output of different energy sources in Britain every day from the 31st of December 2011 to the 3rd of August 2019. The accompanying article describes the declining use of coal-derived energy that the country is experiencing, and it does so mainly with the following graph:

![Image](https://media.data.world/MZv1UvTuRf2sakpA9jJM_Screenshot%202019-08-03%20at%207.53.06%20am.png)

## My thoughts on the visualisation:

### What works with this chart?

- It can be understood quickly and at a glance;
- It uses percentages instead of total values, which helps comprehension if one is not familiar with the topic;
- The stark difference between the mostly black bands in 2012 versus the all-white bands in 2019 makes the point of the visualisation clear and immediate.

### What doesn't work with this chart?

- Colour gradients are usually not a good way to convey quantitative changes, as humans are not as good at discerning differences in saturation and hue as much as they are with lengths and positions on a common axis;
- While the observer gets the general idea the graph is trying to convey, they have no frame of reference for the change they are seeing;
- The separation of the years breaks the continuity of the data;
- The legend only reaches 50% of the total energy output, which can be seen as a kind of axis truncation.

### How can it be improved?

- I thought to transform the graph from a series of bar which separated the individual years to a continuous line graph, which is usually the best way of visualising changes of a variable over time;
- As someone who is not familiar with the topic of energy production myself, I thought adding a frame of reference for the viewer would help comprehension, i.e. plotting the total energy output from coal against all other non-coal sources. This already showed how, even in 2012, the total coal output was much lower than that of alternative sources combined;
- Taking from what did work with the original visualisation, I decided to add a "relative" version of the graph, in which the output of coal and non-coal energy was represented in relation to their sum. This matches what the original visualisation was trying to say, that almost 50% of the energy output in 2012 was composed by coal, but it does so in a way that the 50% is not seen as the "darkest" option possible.
- One thing that my version of the chart fails to do, however, is show the data day-by-day, and, in doing so, we miss out on those days in which coal output reached 0%. However, I feel like the steep drop represented in both graphs is enough to convey the take-home point of "Britain is rapidly phasing out coal".

![Image](https://i.imgur.com/jYnVxUK.png)

[Interactive dashboard](https://public.tableau.com/profile/alepoptosis#!/vizhome/Britainisrapidlyphasingoutcoal-MakeoverMonday/Britainisrapidlyphasingoutcoal)

## How did I do it?
Creating the actual plots was simple enough thanks to Tableau, however I had to create a couple of calculated fields, and a parameter to allow the viewer to compare the coal output to each individual alternative energy, instead of limiting the visualisation to "coal versus others". I feel like this helps the viewer understand how the output of coal alternatives also changed during the years.

I created a parameter which allowed to choose between all the non-coal alternatives, plus an option which grouped them all. Then, I created two dynamic axes which referred to this parameter: 

- Total output: this contained a CASE function which accounted for each choice in the parameter. If there is a better way to do this, please do tell.

```
  CASE [parameter]
  WHEN "Non-coal" THEN SUM([Non-coal])
  WHEN "Solar" THEN SUM([Solar])
```

- Relative output: this referred to the results of the case function, creating a percentage that represented how large the output was when compared to the total. Again, if there's a better way, I'd love to know about it.

```
[total output] / (SUM([Coal]) + SUM([Non-coal])) * 100
```

These two measures were the x axes of the two graphs, and thus changed dynamically depending on the user selection.

## Final thoughts

I really enjoyed this first Makeover Monday. At first, I wasn't even sure I was understanding the data correctly, and I had already started to see bigger, fancier representations than what I had in mind. But then I remembered that simple is often good, and that in the end, finished is better than perfect. So here is my take on this week's data. It might make some good points, it might have some big flaws, but at least it exists - hopefully as the first of many.