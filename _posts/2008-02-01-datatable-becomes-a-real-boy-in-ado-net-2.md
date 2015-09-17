---
layout: post
title: DataTable Becomes a Real Boy in ADO.NET 2
date: 2008-02-01 18:49
author: John
comments: true
categories: [All]
---
<P>I am really excited about some of the new features in ADO.NET 2. I <A href="/blogs/john.papa/archive/2005/03/30/ADO_NET_2_DataTable_Merge.aspx">posted here last month</A> regarding how the ADO.NET 2 DataTable class will expose a Merge method (woo hoo!).&nbsp;I found this very useful when I had DataTable's to merge but no DataSet (and thus had to create a DataSet just to merge the DataTable objects -- yuk!) </P> <P>Anyway, there are other situations where I had a DataTable sans a DataSet and I had to create a DataSet just to take advantage of some features it had that the DataTable didn't. In ADO.NET 2, a lot of attention appears to have been paid to the DataTable as it now has many of the features of the DataSet. For example, in ADO.NET 2 you can get the following method on a ADO.NET 2 DataTable that were formerly only available in a DataSet:</P> <UL> <LI>Merge <LI>ReadXml <LI>ReadXmlSchema <LI>WriteXml <LI>WriteXmlSchema</LI></UL> <P>I never liked how the DataTable did not have the xxxXml method in its arsonal. But at least the next incarnation of ADO.NET will have incldued many of the features that the DataSet already has ... a bit of catch-up, I guess. </P> <P>I'm very excited about the ability to create a DataTable from a DataView, the DataTable's&nbsp;new GetDataReader method, the fact that&nbsp;I can now change the DataRow.RowState&nbsp;manually, and the plethora of other features as well! I'm having fun putting together some code samples for <A href="http://www.ftponline.com/conferences/vslive/2005/bo/">VSLive</A>, <A href="http://msdn.microsoft.com/msdnmag/">MSDN Magazine</A> and <A href="/blogs/john.papa">my codebetter.com blog</A> on these cool ADO.NET 2 features! </P> <P>&nbsp;</P>

