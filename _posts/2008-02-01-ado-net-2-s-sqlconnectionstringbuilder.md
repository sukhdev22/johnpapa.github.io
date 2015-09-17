---
layout: post
title: ADO.NET 2's SqlConnectionStringBuilder
date: 2008-02-01 18:49
author: John
comments: true
categories: [All]
---
<P>The ADO.NET team is working on a building an object called&nbsp;SqlConnectionStringBuilder. The object&nbsp;is intended to assist in building connections string. Pretty basic concept and if you use config files to store your connection strings, you may not take advantage of it (but still could). But if you are writing code that concatenates strings into a connection string, you might want to check out <A href="http://blogs.msdn.com/dataaccess/archive/2005/03/30/403926.aspx">this blog</A>&nbsp;by Sushil&nbsp;Chordia from the ADO.NET team. pretty cool stuff!</P> <P>The code would work like this:</P> <FIELDSET><LEGEND>SqlConnectionStringBuilder</LEGEND><span class="myCode"><span class="myKeyword">public void </span>AccessData(<span class="myKeyword">string</span> serverName, <span class="myKeyword">string</span> uid, <span class="myKeyword">string</span> pwd) <BR>{ <BR>&nbsp;&nbsp;&nbsp;&nbsp;SqlConnectionStringBuilder sqlConStrBldr = <span class="myKeyword">new</span> SqlConnectionStringBuilder(); <BR>&nbsp;&nbsp;&nbsp;&nbsp;sqlConStrBldr.DataSource = serverName; <BR>&nbsp;&nbsp;&nbsp;&nbsp;sqlConStrBldr.UserID = uid; <BR>&nbsp;&nbsp;&nbsp;&nbsp;sqlConStrBldr.Password = pwd; <BR>&nbsp;&nbsp;&nbsp;&nbsp;SqlConnection cn = <span class="myKeyword">new</span> SqlConnection (sqlConStrBldr.ConnectionString); <BR>&nbsp;&nbsp;&nbsp;&nbsp;cn.Open(); <BR>&nbsp;&nbsp;&nbsp;&nbsp;... <BR>&nbsp;&nbsp;&nbsp;&nbsp;... <BR>&nbsp;&nbsp;&nbsp;&nbsp;... <BR>&nbsp;&nbsp;&nbsp;&nbsp;cn.Close(); <BR>} </span></FIELDSET> <P>On a scale of 1 - 5, WOW! factor of&nbsp; 2. But still very useful. Sometimes simple is better!</P> <P class=MsoNormal style="MARGIN: 0in 0in 0pt">&nbsp;</P>

