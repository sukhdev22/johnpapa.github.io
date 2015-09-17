---
layout: post
title: Garbage Collection Quiz
date: 2008-02-01 18:48
author: John
comments: true
categories: [All]
---
Here's a quick quiz about GC: <BR>Q) At what point is x eligible to be cleaned up by the GC? <BR><BR>&nbsp; <FIELDSET><LEGEND>Garbage Collection</LEGEND><BR><FONT color="#000000" size="2"><FONT color="#0000ff" size="2">public</FONT> void foo() <BR>{ <BR>&nbsp;&nbsp;&nbsp;&nbsp;Class1 x = <FONT color="#0000ff" size="2">new</FONT> Class1(); <BR>&nbsp;&nbsp;&nbsp;&nbsp;Class2 y = <FONT color="#0000ff" size="2">new</FONT> Class2(); <BR><BR>&nbsp;&nbsp;&nbsp;&nbsp;y.Width = x.GetWidth(); <BR>&nbsp;&nbsp;&nbsp;&nbsp;y.Height = y.Width; <BR>&nbsp;&nbsp;&nbsp;&nbsp;y.Color = "Red"; <BR>} <BR></FONT></FIELDSET> <BR><BR><B>ANSWER:</B> (highlight the black area to see answer) <BR><FONT style="BACKGROUND-COLOR: #000000" color=#000000>After x.GetWidth() is executed</FONT> <BR><BR>See <A href="/blogs/john.papa/archive/2005/04/02/61096.aspx">this post's comments</A> for explanation/discussion... <BR>

