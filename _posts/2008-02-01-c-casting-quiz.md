---
layout: post
title: C# Casting Quiz
date: 2008-02-01 18:49
author: John
comments: true
categories: [All]
---
<P>There are several ways to convert and cast values in .NET. For example, DirectCast versus System.Convert and if you are a VB.NET'er, you have the CInt, CBool, C<I>xxx</I> functions. It is along these lines that I offer this quiz: What are the differences between&nbsp;the following ways to cast an object?</P> <P>&nbsp;</P> <FIELDSET><LEGEND>Casting quiz</LEGEND><PRE><SPAN style="FONT-SIZE: 9pt; COLOR: black; FONT-FAMILY: Arial"><SPAN style="COLOR: green">/// Technique #1</SPAN> <SPAN style="COLOR: blue">object</SPAN> item = GetIt(); Dog dog = (Dog)item; <SPAN style="COLOR: green">/// Technique #2</SPAN> <SPAN style="COLOR: blue">object</SPAN> item = GetIt(); Dog dog = item <SPAN style="COLOR: blue">as</SPAN> Dog; <SPAN style="COLOR: blue">public object</SPAN> GetIt() { <SPAN style="COLOR: blue">object</SPAN> x = <SPAN style="COLOR: blue">null</SPAN>; <SPAN style="COLOR: green">/// Does something that tries to get an instance of an object</SPAN> <SPAN style="COLOR: blue">...</SPAN> <SPAN style="COLOR: blue">...</SPAN> <SPAN style="COLOR: blue">...</SPAN> <SPAN style="COLOR: blue">return</SPAN> x; } </SPAN></PRE></FIELDSET> <BR>What is the difference between these 2 techniques of casting and when would you want to use one over the other?

