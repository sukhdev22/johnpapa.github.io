---
layout: post
title: Installing SQL Server on 64bit Vista – The Native Client Got Restless
date: 2009-01-31 19:40
author: John
comments: true
categories: [All]
---
<p>Sometimes things go amiss. Sometimes they work out. And sometimes we have no idea why things end up where they do. Today I was installing SQL Server 2005 developer edition on a Vista 64bit PC. I’ve done this dozens of times between 32bit and 64 bit OS’s, including Vista 64bit so there was nothing new here for me. But that did not stop the wild and wacky stuff form happening to the installation.</p>  <p>I ran across this issue where during the installation of SQL Server is failed to install the Database server and the tools (pretty much the keys of what I needed) due to a problem with the SQL Native Client. The error was:</p>  <blockquote>   <p>&quot;And installation package for the product Microsoft Native Client cannot be found. Try the installation again using a&#160; valid copy of the installation package 'sqlncli_x64.msi&quot;</p> </blockquote>  <p>Now, I was installing the 64 bit OS version of SQL Server … and heck, I am human, so I even double and triple checked that. A quick google search found a few issues people have run into similar to mine. The short version of the story is that Visual Studio installed a version of SQL Native Client on my PC that SQL Server did not like. So I had to go into Add/Remove programs and remove SQL Native Client. Then I tried installing the 64bit SQL Server 2005 Developer edition and everything worked.</p>

