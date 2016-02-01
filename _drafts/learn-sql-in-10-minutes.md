---
layout: post
title:  "Learn SQL in 10 minutes"
date:   2015-11-27
categories: DAC
---
# Learn SQL in 10 minutes
<p>Hopefully you’re already convinced that learning SQL is worth it (why would you bother if you didn’t…don’t you have anything better to do?!), but if not check this out first. That’s not part of the 10 minutes, just so you know.</p> 
<p>In the next 10 minutes you’ll learn a method for writing SQL that will initially serve as a crutch to help you hobble through SQL until you internalize the process. Then you’ll be standing on two solid SQL feet. Then you can learn to walk, run, skip and dance with SQL. 
All the background you need</p>
<p>Databases are where we store mass amounts of data. One way of storing data in databases is called relational, which means “a bunch of related, but separate, tables.” SQL is meant for relational databases. Tables have rows (called records) and columns (called fields). A piece of data is stored in a field in a record.
SQL allows us to retrieve records from tables 
within relational databases.</p>

## SQL is easy
SQL is more structured than most programming languages—in fact SQL is short for Structured Query Language. Query means question, and we’re learning how to pose questions that a database can respond to with data. Questions to a database begin with the keyword SELECT.
 
SQL is made up of “clauses” which are pairings of a SQL Keyword (like SELECT) followed by a Reference to the Data from a table in the database. These clauses are always written in the same order.
Learning the order and a few of the special keywords 
is all you need to start writing SQL.
The table below shows the order in which the clauses are written. From here on I’m calling this the SQL Grammar (or Grimoire) Table (SGT), since the word “table” is reserved to mean database table already. SGT is your crutch. Lean on SGT. 
So, in the SGT below, SELECT, FROM and the semicolon (;) are part of every query. All the other clauses are optional and that entire row is skipped if not needed. The description indicates what effect including that clause has on the data that are returned to you. For instance, WHERE filters out data based on a condition; ORDER BY orders data; LIMIT allows us to return a specific number of records.
 
As you can see, type of “reference to the data” is dependent on which keyword precedes it. SELECT is followed by one or more field names from the table that’s specified in the FROM clause. Those field names are the ones you will get back from the database.

SQL Keyword | Reference to the Data | Description
:---|:---|:---|
<b>SELECT</b> | field names separated by commas | The data you want to see |
<b>FROM</b> | table name | The table where the data lives |
WHERE | condition is true | Filters to rows where condition is true |
GROUP BY  | field(s) to group on | Summarize groups of data |
HAVING | condition is true for the group | Filters to groups where aggregate is true |
ORDER BY | field(s) to sort on | Sorts the data |
LIMIT | a number (of rows to return) | Limits to a certain number of rows |
<b>;</b> | not applicable* | ends the SQL statement
 
note: The semicolon isn’t actually a clause, it just ends the statement and so there is no “reference to the data.”

## Examples
We have a table called ‘people’ in our database full of first and last names in fields called ‘first_name’ and ‘last_name’. To get all the records from that table, we use the simplest worthwhile query:

SELECT | first_name, last_name |
FROM | people; |

Starting from the top of the SGT, we write the keyword verbatim, SELECT, followed by the appropriate “reference to the data,” which for SELECT is a list of field names—first_name, last_name. Only place a comma between items in the list, not after the last one. Next we have FROM followed by the name of the table we are accessing from the database. Looks a lot like English, huh? 
We don’t want to invoke any of the special properties of the other SQL clauses such as filtering out records or limiting to a number of rows, so we’re done. We end the statement with the required semicolon and send it off to the database. 
Next let’s get everyone with the same last name together in our data by sorting.

SELECT | first_name, last_name |
FROM | people |
ORDER BY | last_name; |

Again, starting from the top, we always begin with SELECT and FROM—no change there. Skip over all rows in SGT that aren’t necessary until we come to ORDER BY, which we write verbatim, followed by the field name that we want to sort. Multiple fields to sort on are separated by commas just like with the SELECT clause. Sorting can be done for each field ascending (ASC by default) or descending (DESC). ORDER BY last DESC, means sort on lastname from Z-A. 
Next we’ll look at a subset of the ‘people’ table by filtering down to records where the last name is in the first half of the alphabet (all last names beginning with the letters A-M).  
SELECT first_name, last_name
FROM people
WHERE last_name < ‘N’
ORDER BY last_name;
Hopefully you’re starting to get the hang of using SGT and why we just fit the WHERE clause in between FROM and ORDER BY. The “reference to the data” for WHERE is a little different than we have encountered. It’s a condition that for each record in our table is either True or False. When it’s True, that record is included in the data returned to us. There are many options when it comes to conditions and additional keywords that allow you to get just the data you want. We can even combine conditions with AND/OR to be more specific. It’s easy to learn these as you go, but keep in mind that instead of the equals sign we can use the other common symbols (<, >, <=, >=, <>), the last one meaning not equals.
Two more examples will round us out; the second example will build on the first.  Let’s calculate how many records were returned in our last query. Unlike in all previous queries, which returned multiple records of data contained in our table, the query above returns a single row containing the count of records in our query.
SELECT count(1)
FROM people
WHERE last_name < ‘N’
ORDER BY last_name;
There’s only one change to our previous query here. We replaced the two field names in the SELECT clause with the function ‘count’ to which we passed an argument, the number 1. The argument 1 is a SQL convention; what’s important is how it is interpreted.
SQL is all about tables, so whatever you put on the right side of the SELECT clause is what gets returned for every record in our query. Previously, when we had the fields ‘first_name’ and ‘last_name’ in the SELECT clause, it returned those fields for every record. In this case, the number 1 is returned for every record. 
The SQL function ‘count’ can pretty much count anything so it’s just a convention to use the number 1. As we know from using functions to summarize data elsewhere (like Excel), a function takes a bunch of data and turns it into a single number, like the count of rows, and that’s exactly what happens here. SQL calls functions like this, aggregate functions, and includes others like ‘sum’ and ‘avg’ for average. 
In the query above, we can’t mix aggregate functions and field names in the SELECT clause—example: SELECT first_name, count(1) —because the function would attempt to return a single row while the field would try to return multiple rows. That wouldn’t make any sense. If we want to know the count of people with a particular first name, we would need to split our table into groups, which is what we’ll be doing in the last example. 
One last note before we move on, I kept the ORDER BY clause in the query above for consistency and because it will be handy again in the next example. The count of records are not going to change based on how we sort the data, so for efficiency that should be removed. 
OK, in this final example, we’re going to look at groups of data within a single table, which is almost always more interesting for aggregate functions than using the whole table as in the previous example. A group in this case comprises all the records that contain the same value in one field. For instance, if we group on first_name then we have a group for Bob, Karen, Chris, Miguel, Ahmed and so on. Let’s find out which last names are most popular in the first half of the alphabet. We’ll even get rid of any last names that only have a single record in our table, because there are lots of single-occurring names.
SELECT last_name, count(1)
FROM people
WHERE last_name < ‘N’
GROUP BY last_name
HAVING count(1) > 1
ORDER BY count(1) DESC;
Wow, that’s a doozy, right? But we’ve got this, one piece of SGT at a time. 
We added the GROUP BY clause and the right side of that clause is a field name, like we had with SELECT and ORDER BY previously. 
We added last_name to our SELECT list since we want to know which “count” corresponds to which last name. Most of the time when grouping, your SELECT list will contain all the fields in the GROUP BY clause, which are essentially the group’s title, as well as any aggregate functions (yes, there could be more than one). Just like in the previous example, it can’t contain fields that aren’t being either grouped on or aggregated because they would be of different size.
We also included the HAVING clause, which is similar to WHERE in that it contains a condition, but instead of a “row-wise” condition that’s True or False for each record, it contains a “group-wise” condition that’s True or False for each group. For that reason, HAVING conditions use aggregate functions. In this case, we get rid of any groups that don’t satisfy the condition of having a count greater than 1, a single record. 
Lastly, we’re doing something different with the ORDER BY. Namely, sorting by the function count with the highest value at the top by specifying DESC. This will up the most popular name (by count) at the top and the least popular at bottom.
SQL Grammar Table (revisited)
This brings us to the end of the lesson as well as a revised version of the SGT. It now includes a caveat that wherever we have “fields” in our “Reference to the Data” because as we saw in the last couple examples that may instead be an aggregate functions, and in the wild world of SQL, many other options exist.
SQL Keyword
Reference to the Data
Description
SELECT
field names* separated by commas
The data you want to see
FROM
table name
The table where the data lives
WHERE
condition is true
Filters to rows where condition is true
GROUP BY 
field(s)* to group on
Summarize groups of data
HAVING
condition is true for the group
Filters to groups where aggregate is true
ORDER BY
field(s)* to sort on
Sorts the data
LIMIT
a number (of rows to return)
Limits to a certain number of rows
;
not applicable
ends the SQL statement

## Stuff you need to know for the real world
There are two types of databases: file-based and server-based. A file-based database is housed completely within your computer in a single file. A server-based database is a piece of software that sits on another computer. To interact with this type of database, you use a client (a piece of software on your computer that couples with the piece of software on the other computer) to connect to the server and then send a SQL statement over the connection and receive data back. For obvious reasons, server-based databases are more difficult to set up, but are more commonly used in the real world because multiple users can easily connect to and use the same database. File-based databases are simple to set up and great for practicing SQL and for when you’re the only one who needs to access the data.

You can live without this, but probably shouldn’t
One thing I have neglected to mention thus far and that is typically the first query a beginner learns is what’s called “select star.” The so called “star” in SQL is the asterisk character and is shorthand for returning the entire record (all the fields). It’s only used in the SELECT clause, and some people say count(*) instead of count(1), meaning count the record. The following query returns the first 100 records containing every field in the people table.
SELECT *
FROM people
LIMIT 100;
The reason I avoided mentioning it until now is that the star character seems to cause a lot of confusion for beginners, and it’s not even a good practice except when first exploring a table to avoid typing out all the field names. You will encounter it, and so when you do, now you know.
