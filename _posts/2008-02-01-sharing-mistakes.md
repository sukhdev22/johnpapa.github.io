---
layout: post
title: Sharing Mistakes
date: 2008-02-01 18:40
author: John
comments: true
categories: [All]
---
<p>With VB 6 and ADO 2.x I can't tell you how many times I wrote the following type of code and only realized what I had done <b>after</b> I had pressed F5:<br />
<br />
&nbsp;</p>
<fieldset><legend>The Infamous Infinite Loop Blunder</legend><font face="Courier New" size="2"><br />
'--- Using VB 6 and ADO 2.x <br />
oRs.Open <br />
Do While Not oRs.EOF <br />
&nbsp;&nbsp;&nbsp;&nbsp;Debug.Print oRs(0) <br />
Loop <br />
</font></fieldset>
<p><br />
<br />
Usually the moment after I ran this code I would realize that I was in an infinite loop. Then I would quickly put in the oRs.MoveNext just before the end of the loop and all would be well. Fortunately, in ADO.NET I no longer have this problem thanks to the DataReader and how it reads a record and moves the cursor to the next position all in one fell swoop. So .NET saved me from one of my most infamous blunders. <br />
<br />
&nbsp;</p>
<fieldset><legend>Using C# and ADO.NET</legend><font face="Courier New" size="2"><br />
SqlDataReader oDr = oCmd.ExecuteReader(); <br />
<font color="#0000ff">while</font>(oDr.Read()) <br />
{ <br />
&nbsp;&nbsp;&nbsp;&nbsp;Console.WriteLine(oDr[0]); <br />
} <br />
</font></fieldset>
<p><br />
<br />
But of course I didn't get off that easy. I now have all new mistakes to make with .NET. My most common mistake these days occurs when I declare a variable inside of a &quot;try&quot; block and then use it outside of the &quot;try&quot; block. For example, I'll do something along the lines of the foo method below: <br />
<br />
&nbsp;</p>
<fieldset><legend>Oops!</legend><font face="Courier New" size="2"><font color="#0000ff">public int</font> foo(<font color="#0000ff">int</font> y, <font color="#0000ff">int</font> z) <br />
{ <br />
&nbsp;&nbsp;&nbsp;&nbsp;<font color="#0000ff">try</font> <br />
&nbsp;&nbsp;&nbsp;&nbsp;{ <br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#0000ff">int</font> x = y * z; <br />
&nbsp;&nbsp;&nbsp;&nbsp;} <br />
&nbsp;&nbsp;&nbsp;&nbsp;<font color="#0000ff">catch</font> <br />
&nbsp;&nbsp;&nbsp;&nbsp;{ <br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#008000">// catch it here</font> <br />
&nbsp;&nbsp;&nbsp;&nbsp;} <br />
&nbsp;&nbsp;&nbsp;&nbsp;<font color="#008000">// this will not compile!</font> <br />
&nbsp;&nbsp;&nbsp;&nbsp;<font color="#0000ff">return </font>x; <br />
} <br />
</font></fieldset>
<p><br />
But at least with this mistake I catch it when I build my C# project. Then I move the declaration of the variable x outside of the try block and all is well. <br />
<br />
OK, so now that I have opened up and shared some of my embarassing blunders, it's time for you to share some of your common blunders. Don't be shy!<br />
&nbsp;</p>

