---
layout: post
title: Clarifying ADO.NET 2 Batch Updates
date: 2008-02-01 18:49
author: John
comments: true
categories: [All]
---
<P>Pablo Castro, Microsoft's Program Manager of the ADO.NET Team, <A href="http://blogs.msdn.com/dataaccess/archive/2005/05/19/420065.aspx">has a good post last week</A> that helps clarify how bath updates are intended to work in ADO.NET 2. This is a common discussion that I am drawn into since the DataAdapter actually invokes its command for each modified row in the DataTable that it is associated with. Thus if you have a DataTable with the following deltas:</P> <UL> <LI>7 modified rows <LI>2 added rows <LI>2&nbsp;deleted rows</LI></UL> <P>The DataAdapter will invoke the UpdateCommand 7 times, the InsertCommand 2 times and the DeleteCommand 2 times for a total of 11 round trips. There are several ways to work around this, some of which Pablo points out such as sending all of the SQL statements down at once manually. You can also use diffgrams using <A href="http://msdn.microsoft.com/msdnmag/issues/05/06/DataPoints/">SQL Server's XML features</A>, too. But none of the solutions is as elegant as how ADO.NET shoulda, coulda , woulda handled it. Kudos to Pablo for a good explanation!</P>

