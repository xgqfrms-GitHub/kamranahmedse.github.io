---
layout: post
title: SQL - `IN` operator with combination of columns
comments: true
---
If you write SQL queries often, you should have probably used the `IN` operator which determines if a specified value matches any value in a list or a subquery. Below is the most simple use-case with single value, for examle:

<pre><code class="sql">
SELECT	* 
FROM 	`students`
WHERE 	id NOT IN (1,5,6,3)
</code></pre>

But one thing that you might not know is that you can use that for a combination of values as well. For example lets take a table where there are student names and subjects

![Users Table](http://i.imgur.com/3BuINvu.png)

And there are some user and subject combinations that we do not want, lets say below are the ones that we do not want:

![Not Required Columns](http://i.imgur.com/BYoGdkU.png)

In that case, our SQL would look like the following:

<pre><code class="sql">
SELECT * 
FROM   students 
WHERE 
	( name, subject )
NOT IN 
	(
		('Jane Doe', 'Analysis of Algorithms'),
		('John Doe', 'Software Engineering - II'),
		('Jane Doe', 'Professional Practices')
	);
</code></pre>

The list used in `NOT IN` might be provided in the form of list i.e. the way it is provided in the above example or it might be returned from some subquery.