---
layout: post
title: Debug With TypeScript 0.8.1
date: 2012-11-15 22:13
author: John
comments: true
categories: [javascript, typescript, Uncategorized]
---
<a href="http://blogs.msdn.com/b/typescript/archive/2012/11/15/announcing-typescript-0-8-1.aspx" target="_blank">TypeScript 0.8.1 was just released</a> and it now supports debugging right inside Visual Studio! You can <a href="http://blogs.msdn.com/b/typescript/archive/2012/11/15/announcing-typescript-0-8-1.aspx" target="_blank">read more about TypeScript and its latest changes in this post</a> by Luke Hoban, PM of the TypeScript team and <a href="http://www.microsoft.com/en-us/download/details.aspx?id=34790" target="_blank">you can download TypeScript from here</a>.
<blockquote>TypeScript is a super set of JavaScript and brings optional static typing and other features like classes to the picture.</blockquote>
You can learn more about TypeScript in my upcoming course which I am co-authoring with Dan Wahlin for Plrualsight (coming later this year!).

<img class="aligncenter" title="TypeScript Debugging" src="http://blogs.msdn.com/resized-image.ashx/__size/550x465/__key/communityserver-blogs-components-weblogfiles/00-00-01-56-67/4130.debuggreeter.png" alt="" width="550" height="354" />
<h2>Update (11/22/2012)</h2>
I was having some difficulty getting the debugging to work, so I thought I might share what I found after talking to the TypeScript team (great guys, BTW). There are a few requirements to get debugging to work:
<ul>
	<li>Visual Studio 2012</li>
	<li>TypeScript 0.8.1</li>
	<li>Internet Explorer 9 or 10</li>
</ul>
Also, some earlier versions of Web Essentials 2012 may interfere with the TypeScript debugging. The good news is that Mads (program manager for Web Essentials) has quickly updated it and there is now a version that works great with TypeScript 0.8.1. I have had much success using Web Essentials 2012 version 1.8.8.1. I've also been able to debug TypeScript 0.8.1 code when no Web Essentials was installed.

The best news is that the  TypeScript team and the Web Essentials teams mentioned to me that they will try to synch releases moving forward.

Happy debugging!
