---
layout: template
title: Makeover Monday 2019/W38
sub_title: Positive Impact Events
---

# Makeover Monday 2019/W38 - Positive Impact Events

This week's Makeover Monday was in collaboration with the UN SDG Action Campaign in occasion of the upcoming Global Goals week. Positive Impact Events collected data through a survey which asked people to propose specific actions that the global event industry can take to help the effort towards achieving the [Sustainable Development Goals](https://www.un.org/sustainabledevelopment/sustainable-development-goals/) set by the UN in 2015. More specifically, the survey asked people to pick what they think are the 5 most crucial goals among the total 17, and then suggest possible actions and their duration relatively to each of the chosen goals. The survey also collected data about the voter's country and city of origin, their age, gender, education level, disabilities, and job role. The original visualisation was made in Google Data Studio and it looks like this:

![Image](https://media.data.world/GADNAjpKQW263emC28EP_original.png)

## My thoughts on the visualisation:

### What works with this chart?

- ... **Not much**. It is a good idea to show the top two actions for each goal and the durations that people proposed for them, but that is pretty much it. 

### What doesn't work with this chart?

- The **filtering system is slow** and it is difficult to isolate a specific group of voters. Also, there is **no overview of the votes**, which means that anyone interested in the top goals/suggestions for a group would have to individually go look for the change in results for each of the 17 goals;
- Navigating the other proposed actions is difficult as they are represented as a **table instead of a list**, so the viewer has to hover over each block to read the results;
- Overall, this visualisation is better suited for someone who is going to work with the data and wants to study it through something other than a table, but otherwise **it struggles to communicate content effectively** as it is.

### How can it be improved?

My mistake at the beginning of this Makeover Monday was to try and fit too many things in the same dashboard. Between the top actions per goal, the proposed duration for those actions, and the choice of goals per country and population group, there is a lot of information to draw from this survey. However, to fit it all into one visualisation means overloading your viewer and giving them a bad time.

Instead, I chose to focus on a specific angle: how did people from different countries, age groups, genders, education levels etc. prioritise the different goals? This information is conveyed by just two graphs, a world map indicating the top goal voted by each country, with the bubble size indicating the number of voters, and a scatter plot indicating what percentage of each voter group selected each goal as one of their top 5.

The viewer can hover over each data point to see a short description of the voter group and their preferences to better understand the smaller details of the results, but overall they should be able to quickly get a general idea of which goals people find most important, and how this changes with different voter groups.

![Image](https://i.imgur.com/mBDXHru.png)

[Interactive dashboard](https://public.tableau.com/profile/alepoptosis#!/vizhome/PositiveImpactEvents-MakeoverMonday2019W38/PositiveImpactEvents)

## How did I do it?

I spent about three days on this one and I am happy to say I have learned a few new things.

- First of all, I loaded the data in Python because the fact that the countries were all lowercase and the goals all uppercase was bothering me to no end, and there was no way I was manually changing all the aliases. While I was there, I also merged the actions table, containing all the main information, with the goals table, containing the goal description for each goal ID. This is the code I used:

```
# load the tables
actions = pd.read_csv("Positive Impact Events - Actions.csv")
goals = pd.read_csv("Positive Impact Events - Goals.csv", header=None, names = ["Goal", "Goal name"])

# left join the tables (in my head, "pie" stood for "positive impact events". don't judge me.)
pie = actions.merge(goals, how='left')

# fix the case
columns_to_change = ["Country", "Goal name"]
for col in columns_to_change:
    pie[col] = pie[col].str.title()
```

- Next up, I spent an entire day fighting with Tableau because I could not for the life of me find a way to make the map show the most popular goal for each country (the "mode"). Somehow, using `INDEX()` would work in a normal table, but once I switched to a map visualisation Tableau would show the top alphabetical goals instead of the most voted goals. In the end, I got so frustrated that I re-opened python, re-loaded the data and created a separate dataset for each country, its mode, and the number of votes it received (to retain the bubble size), and used it to create the map visualisation. This is the code I used:

```
# number of votes per goal per country
top_goal_count = pie.groupby(["Country"])["Goal name"].value_counts().to_frame("Votes")

# keep only top value per country
top_goal_count = top_goal_count.groupby(["Country"])["Votes"].nlargest(1).to_frame()
```

**Note**: for some reason, this code results in a dataframe with two "Country" columns. I have no idea why nor how to not make it do that. If anyone can tell me what I am doing wrong I would wildly appreciate it. Either way, it works, even if in a dirty way.

**Further note**: some countries are multimodal, i.e. there is more than one most popular goal. For those situations I simply let Python pick any one of them, since this was mostly caused by a very low number of voters, who all chose different goals.

Unfortunately, using a separate dataset for the map meant that I could not use it as a filter for the scatter plot. It would have been cool to see the composition of voters of different countries, but because they were separate tables, I did not know how to make that happen.

- Finally, I learned how to do a neat thing that I ended up not using in the final visualisation: I managed to turn the SDG icons into interactive filters by using custom shapes and an extremely tweaked treemap! I was sad not to use them but they ended up making everything too cluttered. If you're interested in how I did it, here's an [unlisted Tableau dashboard](https://public.tableau.com/profile/alepoptosis#!/vizhome/Notes-Interactiveicons/Selectgoal?publish=yes) which you can play with and download.

## Final thoughts

Oh boy am I glad this is done. Because of the amazing opportunity to have our visualisations shown at the UN General Assembly, I ended up spending multiple days on this, trying to make it interesting and appealing. As I mentioned, at first things were way too cluttered, with me trying to show off all the cool insight I had found in a single dashboard. It kept looking horrible. Luckily I realised I needed to take a step back, cut some information away, and stay minimal. Another big thanks to [@AdamMico1](https://twitter.com/AdamMico1) for helping me style the horrible mess that this dashboard was when I first contacted him, and to my friends who ended up being my rubber ducks during these past few days. Time to rest now!