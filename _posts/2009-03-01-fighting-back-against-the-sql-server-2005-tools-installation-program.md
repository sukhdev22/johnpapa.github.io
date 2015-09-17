---
layout: post
title: Fighting Back Against the SQL Server 2005 Tools Installation Program
date: 2009-03-01 14:37
author: John
comments: true
categories: [All]
---
<p>There is a funky problem that sometimes sticks its ugly head out and bites you when trying to install SQL Server 2005 and its tools. I’ve hit this a few times when installing, but not every time. When installing SQL Server 2005, its databases and its tools sometimes the client tools do not get installed even when you check the box for this option. Then you go to the Start menu and look for the tools and they are not there! So then you go try to install them again, thinking maybe you did not check that box. This time it says the tools are already installed so there is nothing for the install program to do. Now the growling begins.</p>  <p>I’ve read some interesting theories behind why this happens, mostly revolving around how the main SQL installer does not run the tools installer properly. I just want my tools installed :-). I have enough to do without worrying about installing software all day long.</p>  <p>The solution is to go to the Tools folder on your installation CD (or DVD) and run the Tools install program directly. Your path may vary of course, but on my CD it was located at this path.</p>  <p>&#160;</p>  <blockquote>   <p><em>E:\ENGLISH\SQL2005\DEVELOPER\SQL Server x64\Tools\Setup\SqlRun_Tools.msi</em></p> </blockquote>  <p>&#160;</p>  <p>Notice I am running the english 64bit version of SQL Server 2005 Developer edition. The executable to install the tools is named <em>SqlRun_Tools.msi</em></p>  <p>&#160;</p>  <p>I hope this helps someone save some time and growls :-)</p>

