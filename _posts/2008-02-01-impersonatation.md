---
layout: post
title: Impersonatation
date: 2008-02-01 18:48
author: John
comments: true
categories: [All]
---
Quick blog for now ... I set up a new ASP.NET project, turn on NT auth, turn off anonymous access, write some ADO.NET code to connect to SQL Server via integrated security and viola! I get this lovely error: <P></P><BR><BR> <FIELDSET><LEGEND>Arg!</LEGEND> <H2><I>Login failed for user 'LANCELOT\ASPNET'.</I> </H2><FONT face="Arial, Helvetica, Geneva, SunSans-Regular, sans-serif"><B>Description: </B>An unhandled exception occurred during the execution of the current web request. Please review the stack trace for more information about the error and where it originated in the code. <BR><BR><B>Exception Details: </B>System.Data.SqlClient.SqlException: Login failed for user 'LANCELOT\ASPNET'.<BR></FONT></FIELDSET> <P> <BR><BR>Easy fix of course. Just need to add this line of code to my web.config file. One would think that after doing this repeatedly that Pavlov would learn. <BR></P> <FIELDSET><LEGEND>Impersonate me</LEGEND><BR><BR>&lt;identity impersonate="true/&gt; </FIELDSET> <BR>

