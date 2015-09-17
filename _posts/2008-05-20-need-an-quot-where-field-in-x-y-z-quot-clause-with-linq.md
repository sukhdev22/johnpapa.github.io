---
layout: post
title: Need a "WHERE field IN (x, y, z)" Clause with LINQ
date: 2008-05-20 23:34
author: John
comments: true
categories: [All]
---
<p>A colleague and I were talking about some LINQ features yesterday and one of the topics that came up was how to implement an IN clause. Ya know, similar to how SQL statements can use an IN clause in the WHERE clause like this:</p>
<p>SELECT city FROM Customers WHERE state IN ('FL', 'NY'', 'NC')</p>
<p>Then I remembered <a href="http://weblogs.asp.net/dwahlin/archive/2008/05/09/using-linq-to-perform-quot-where-in-value1-value2-quot-queries.aspx">Dan Wahlin's post</a> on a similar topic where he shows the following solution (from Dan's post):</p>
<p><font color="#0000ff">The code uses the Contains() method to search for a specific ProductID within the collection which ends up creating a WHERE IN type query.&nbsp; You can do the same thing with LINQ:</font></p>
<pre><font color="#0000ff">public static Product[] GetProducts(Guid[] prodIDs)
{
return (from p in GetProducts()
where prodIDs.Contains(p.ProductID)
select p).ToArray&lt;Product&gt;();
}</font></pre>
<p>The idea here is that the LINQ query is written normally (meaning the from and the select clauses reference the objects). Then the where clause in the LINQ query operates on an array of values. The array of values contains the values you would put in the IN clause. The array supports standard query operators so you can use the Contains method on the array and pass in the value you want to look for.</p>

