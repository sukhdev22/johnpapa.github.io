---
layout: post
title: Fixing SQL Server Reporting Services
date: 2008-02-01 18:51
author: John
comments: true
categories: [All]
---
<P>So I install Visual Studio.NET 2005 side by side with VS.NET 2003 on my computer and things are running smoothly. But then I see that a project that interacts with Reporting Services hits a brick wall. </P> <P><EM><FONT color=#ff0000>Error rsReportServerDisabled : The report server cannot decrypt the symmetric key used to access sensitive or encrypted data in a report server database. You must either restore a backup key or delete all encrypted content and then restart the service.</FONT></EM> </P> <P>After a few brief searches on the web it seems that the installation of VS.NET 2005 which updates some ASPNET account information can cause this problem. The confusing part is that most of the MSDN documentation tells you how to avoid this issue by going back in time and backing up your encrypted keys using the rskeymgt utility. Too bad I don't have a time machie to do that. Another article talks about deleting your encrypted data and then restoring the keys using hte same utility. Finally I found some information on how to reactrivate the report server and fix this problem using the following command:</P> <P><EM><FONT color=#000080>C:\Program Files\Microsoft SQL Server\80\Tools\Binn&gt; rsactivate -r -c"C:\Program Files\Microsoft SQL Server\MSSQL\Reporting Services\ReportServer\RSReportServer.config"</FONT></EM></P> <P>(Obviously you substitute your installation location with what mine are in the above command.)</P> <P>Anyway, this fixed everything for me and I hpoe it helps save you some time if or when you run into this issue with Reporting Services.</P>

