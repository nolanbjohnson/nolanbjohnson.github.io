---
layout: post
title:  "Citi Bike Data: Part 1"
date:   2015-09-03
categories: DAC
---
# Project 1 - Citi Bike Recommendation

Let's visualize some Citi Bike data! We have one month's worth of data to work with and we're interested in understanding the breakdown of rides by sex (male and female) to help inform our decision of how many male- and female-specific bikes to purchase.

First, a little background about [Citi Bike](https://www.citibikenyc.com/) (because being knowledgeable about your data is the most important part of being a good data analyst). It's a bike rental program in NYC. There are [many others](https://en.wikipedia.org/wiki/List_of_bicycle-sharing_systems) like it around the world, and they all work pretty similarly. Renting a bike from a station requires an "access pass." They offer a 24-hour, 7-day and annual pass. After checking a bike out from a station, you have an allotted amount of time (e.g., 30 mins) to check into another station to avoid an additional fee. You can check a bike out again immediately, but this time limit keeps bikes in circulation by penalizing long rides or taking the bikes outside of the coverage area. 

There are [lots of interesting questions](https://github.com/BetaNYC/Bike-Share-Data-Best-Practices/wiki/CitiBike-NYC-Tools-and-Apps) that we can ask using this data (see [extra challenge](#extra-challenge) below). If you'd like to get the raw data from which you are using a small subset, you can find that [here](https://www.citibikenyc.com/system-data). Fair warning, these files are quite large! Each month includes about a million rides. It's definitely possible to use Excel to look at this data for one month, but more than one and you would probably start to see Excel stress.


Getting back to the project prompt, a breakdown of rides by male and female riders:

 Gender | Frequency
:---|---:|
 Male 	| 16 | 
 Female 	| 37 | 

Here are the steps that got us here:
 
1.	We summarized the data, likely with one of the methods below, and put the results in a table.
	*	Pivot table
	*	COUNTIF formula (if you don't know how to do this one, ask your mentor!)
	*	Highlight cells and check the quick stats at the bottom of the workbook. This way works, but it goes against my rule, **Make Excel Do The Hard Stuff, So You Don't Have To!**
2. 	We selected our data and inserted a column chart from the Excel ribbon. From here on, I'll be referring to it as a bar chart even though Excel has given a vertical bar chart a special name.
  
Let's pick up from there and make some conscious design decisions to improve the quality of our chart.

[![click for full video](http://circuits-assets.generalassemb.ly/prod/asset/1821/unit1.gif)](http://recordit.co/ScLpUcZ6JA)

As you can see, step by step we reformatted, removed or added default chart elements. There's no one correct answer when it comes to chart design; the important thing is that we make choices ***for a reason***. Hopefully you agree with some of those choices and can see why the final design is an improvement over default. 

A quick outline of some of the steps:

1.	Removed or reduced the prominence of lines that weren't providing real value to the visualization. It's difficult, but not impossible to go too far with this. My recommendation is to remove until it becomes apparent that you've lost something important.
2.	Removed the legend and instead directly labeled the bars.
3.	Improved the readability of the most important aspects of the visualization--the data.
  
See [Data Looks Better Naked](https://darkhorseanalytics.com/blog/data-looks-better-naked/) for an excellent overview of this method applied to a more egregiously bar chart.


# Extra Challenge  

*	Could we find a way to calculate how much income Citi Bike receives from the riders in our data set?
	*	Remember, there is a price for an access pass as well as [additional charges](https://www.citibikenyc.com/pricing) if you keep the bike out too long.
	*	Do we have all the data we need? If not, what are we missing? Could we make some assumptions or guesses that could get us closer to the answer?
	*	Do we have the data needed to answer a subset of the larger question?
