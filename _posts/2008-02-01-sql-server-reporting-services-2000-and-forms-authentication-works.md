---
layout: post
title: SQL Server Reporting Services 2000 and Forms Authentication Works!
date: 2008-02-01 18:51
author: John
comments: true
categories: [All]
---
<P>Wow. Several days of anguish is finally paying off. My colleagues and I have been trying to implement a SSRS 2000&nbsp; with a web site using Forms Authentication and it is not as easy as you might think. It certainly hasn't been for us. Microsoft's own documentation is built upon Windows Integrated security which is awesome, but not always practical. They also expand on it by offerring examples on how to use Forms Authentication with SSRS 2000 by expanding on the SSRS archtitecture. Their examples aren't bad at all, actually they helped quite a bit. But they did not take us all the way home. We had to improvise on how to pass the credentials and then parse them on the SSRS side.</P> <P>Anyway, I'll be blogging more about this fun weekend (was there a holiday to enjoy?) once I take a breather. But I wanted to get this poost out to say "Yes! You can use Forms Authentication with SSRS!!!"</P> <P>&lt;collective sigh/&gt;</P>

