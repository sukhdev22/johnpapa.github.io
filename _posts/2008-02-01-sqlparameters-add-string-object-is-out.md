---
layout: post
title: SqlParameters.Add(string, object) is Out!
date: 2008-02-01 18:49
author: John
comments: true
categories: [All]
---
<P>One of the pleasures of working with Beta products is just when your code is working, you find out a method is renamed, its overloads have changed or sometimes its just plain gone. Its part of the sport of development. Being the geek that I am, I actually enjoy running into this once in a while in Beta. Keeps me on my toes. (OK, I know I’m weird). Anyway, ADO.NET’s <EM>SqlParameters.Add(string, object)</EM> method is being deprecated in ADO.NET v2.</P> <P>An interesting blog by <A href="http://weblogs.asp.net/jackieg/archive/2005/03/22/395517.aspx" target=_blank>Jackie Goldstein</A> that points out <STRONG>why </STRONG>this method is being deprecated in ADO.NET v2. At first I was like "WHAT!", but it makes more sense after you read the reasoning behind it. However, you can still achieve the same old functionality by using the new ADO.NET v2&nbsp;<EM>SqlParameters.AddWithValue(string parameterName, object value)</EM></P> <P>I have to say that Pablo Castro and the ADO.NET Team have been excellent at helping explain why certain ADO.NET changes are coming. I certainly appreciate it.&nbsp;&nbsp;Kudos to you guys!</P>

