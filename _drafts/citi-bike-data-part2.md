---
layout: post
title:  "Citi Bike Data: Part 2"
date:   2015-09-03
categories: DAC
---
Let's visualize some __more__ Citi Bike data! We have three months worth of data and we want to know the number of trips for both males and females. A line chart should work perfectly. Just as with Part 1 (see previous lecture notes), we could very easily show this in a table, but this time it's actually easier to see the relationship and trend as two lines.

 Gender | June | July | August 
:---|---:|---:|---:
 Male 	| 20 | 25 | 26 
 Female 	| 30 | 27 | 25 

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