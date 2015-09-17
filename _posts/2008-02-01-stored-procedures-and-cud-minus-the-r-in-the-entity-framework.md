---
layout: post
title: Stored Procedures and CUD (minus the R) in the Entity Framework
date: 2008-02-01 18:53
author: John
comments: true
categories: [All]
---
<p>The <a href="http://blogs.msdn.com/adonet/archive/2007/03/08/using-stored-procedures-for-change-processing-in-the-ado-net-entity-framework.aspx">Data Access Team published a great post</a> that has some superb explanations on <a href="http://blogs.msdn.com/adonet/archive/2007/03/08/using-stored-procedures-for-change-processing-in-the-ado-net-entity-framework.aspx">how to make the Entity Framework use stored procedures for inserts, udpates and deletes</a>. (It does not yet support stored procedures for retrieving data.) &nbsp; Obviously there are pieces missing, as Shyam states (such as retrieving data via sprocs), but to see CUD (minus the R) working in the EF with sprocs is great. </p><p>One knock I can already hear though is how people will have to change the existing sprocs. Specifically in the example where the additional parameter must be added to support the EF&#39;s&nbsp; determination of which entities/sprocs to execute in which order. Obviously it would be better if a future evolution could do without this. </p><p>Fantastic to see sproc support born in the <a href="/blogs/john.papa/archive/2007/03/05/Entity-Framework-and-Object-Services-Primer.aspx">Entity Framework</a>!</p><p>On a related note, I am having a heck of a time trying to get an overview of ADO.NET Orcas to fit into a publishable article. There is just sooooo much to it and so little space to write about it. I could go on for days on this topic :)</p>

