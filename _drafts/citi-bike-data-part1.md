---
layout: post
title:  "Citi Bike Data: Part 1"
date:   2015-09-03
categories: DAC
---
Let's visualize some Citi Bike data! We have one month's worth of data to work with and we're interested in understanding the breakdown of rides by sex (male and female) to help inform our decision of how many male- and female-specific bikes to purchase.

First, a little background about Citi Bike. It's a bike rental program in NYC that allows users to rent a bike and ride between stations. If you arrive at the next station within an allotted time (e.g., 30 mins) and check your bike in, you avoid an additional time-based fee. You can check a bike out again immediately, but this time limit keeps bikes in circulation by penalizing taking long rides and taking the bikes outside of the coverage area. There are lots of interesting questions that we can ask using this data. If you'd like to get the raw data from which you are using a small subset, you can find that [here](). Fair warning, these files are quite large! Each month includes about a million rides. It's definitely possible to use Excel to look at this data for one month, but more than one would probably be starting to stress the limits.

 Gender | June | July | August 
---|---|---|---
 Male | 20 | 25 | 26 
 Female | 30 | 27 | 25 

Here are the steps that got us here:

*	We consolidated the data from three separate sheets down into a single data set. Consolidating data is an important first step so that we can use time-saving Excel features like formulas to summarize the data.  
*	We summarized the data, likely with one of the methods below, to come up with the number of riders for each gender and month.
	*	Pivot Tables
	*	COUNTIF formula (if you don't know how to do this one, you should!)
	*	Highlight cells and check the quick stats at the bottom of the workbook
* 	Importantly for the next step, we put those numbers into a table with months along one edge and gender along the other.
* 	We inserted a line chart.

We'll pick up from there and make some conscious (and hopefully good) visualizations decisions to improve the quality of our chart. 

![]({{ site.url }}/assets/unit2.gif)

You can see that we did a few things to take the default chart that Excel spits out to be more like the chart design on the left.

Namely, we:

*	Removed or reduced the prominence of lines that weren't providing real value to the visualization. It's actually difficult, but not impossible to go too far with this.
* Removed the legend and instead directly labeled the lines. With line charts, this is almost always an improvement.
* Improved the readability of the most important aspects of the visualization--the numbers and the line chart.