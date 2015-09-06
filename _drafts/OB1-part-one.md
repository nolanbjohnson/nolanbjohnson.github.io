---
layout: post
title:  "On building a database-driven Excel tool: Intro"
date:   2015-4-20
categories: project
---

When I decided to build a tool to help my company track the progress of their projects, I only had a couple of things figured out. 

1. I knew that we would first deal with the data that would drive the tool, since that's the most common pitfall that I encountered with other projects--they would build a nice fancy something on top of a bog of data and were then surprised as the foundation sunk into the quagmire. 
2. We would use Excel as the primary user interface. This was a pragmatic choice, if not ideal for our purposes, for a handful of reasons. First, I had spent the prior five years accumulating a set of Excel skills that I could bring to bear on this problem. Second, Excel is ubiquitous in the workplace (unlike, say MS Access), and familiarity could work to our advantage. Lastly, it would allow us to quickly create a design without dealing with low-level details--essentially test out the idea and learn what works before investing in a bigger, better solution.

Most everything that went into the solution was either stolen or learned on a previous project (i.e., stolen from I don't know where). There is perhaps only 1% of the project that I could claim was an idea of my own, and by that I mean I did not knowingly pick it up from something I've seen. Nonetheless, I found quickly that both the art and science of creating a tool like this was not the components used, but how to get it all to work together. There are few resources out there that go beyond a simple Excel macro or function and talk about how to make it all function in concert. In addition to sharing a few of my own inventions, that's the purpose I hope this series of posts will serve.

##Here's the breakdown:
* Separation of duties: the data interface
* Stored Procedures & CRUD
* Tables
* Slicers/User Interface
* Shapes