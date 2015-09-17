---
layout: post
title: HotTowel 1.1 with Durandal 2 Now Available
date: 2013-09-05 04:14
author: John
comments: true
categories: [breeze, durandal, hottowel, Uncategorized, visual studio 2012]
---
In the past 7 months since I introduced HotTowel as a way to jump-start SPA development, Visual Studio has evolved as have some of the key JavaScript libraries. Today you can now download an updated HotTowel Visual Studio template. I created 2 different templates base don how Visual Studio has evolved: one for Visual Studio 2012 and one for Visual Studio 2013 preview. You can grab them here (and please rate them on the Visual Studio Gallery):

<ul><li>Download the <a href="http://jpapa.me/hottowel12" target="_blank">HotTowel SPA project template for Visual Studio 2012</a> </li>
<li>Download the <a href="http://jpapa.me/hottowel13" target="_blank">HotTowel SPA project template for Visual Studio 2013</a> </li></ul>

If you like these templates, join me in thanking <a href="https://twitter.com/xinqiu" target="_blank">Xinyang Qiu</a> of Microsoft who helped me get through some of the more confusing parts of creating the templates. :)

<img alt="" src="http://johnpapa.net/wp-content/images/HotTowelPreview.png" />

Hot Towel creates a great starting point for building a <a href="http://johnpapa.net/spa" target="_blank">Single Page Application (SPA)</a> with ASP.NET. Out of the box you it provides a modular structure for your code, view navigation, data binding, rich data management and simple but elegant styling. It provides everything you need to build a SPA, so you can focus on your app, not the plumbing.
<blockquote>Learn more about building a SPA from <a href="http://johnpapa.net/spa?vsix">my videos, tutorials and Pluralsight courses</a>.</blockquote>

<h2>Changes</h2>
Why the changes? First, Visual Studio evolved with 2013 so I wanted to make sure the templates still worked. There were some changes under the covers that you won;t care about that just make it work in 2013 :)

Second, the the Visual Studio Gallery now works with the MVC and SPA project templates. So I wanted to get it up on the gallery (see the links above).

Third, and most importantly to you, <a href="http://www.durandaljs.com" target="_blank">Durandal </a>and Breeze have evolved. Durandal is now at version 2.0 and has breaking changes from its 1.x predecessor. The changes are all good, but they are still changes. So the new template includes the changes and comments explaining what the Durandal code does. Breeze, Toastr, and the other libraries evolved as well, so I updated those and tested them too. For those wanting Bootstrap v3, you'll have to wait a little longer ... I'll get to that, but for now I included Bootstrap 2.3.2. But it is coming to HotTowel.

Fourth, I updated <a href="http://www.nuget.org/packages/HotTowel/" target="_blank">HotTowel for NuGet</a> (if you don't want a template, just grab the NuGet package)

And finally, I am working on a similar template for Angular (maybe HotTowel NG ?). Look for this in the coming weeks as I get closer to releasing my next <a href="http://www.pluralsight.com" target="_blank">Pluralsight</a> course.

As always, you can <a href="http://johnpapa.net/hottowel" target="_blank">find all you need to know about HotTowel on my HotTowel landing page</a>.

<h2>Update</h2>
Eventually we should be seeing a more unified "One ASP.NET" approach when creating a project. Scott Hanselman has been a big driver behind this effort. i expect that is one reason why currently in the VS 2013 Preview the ASP.NET templates are now under a <code>Visual Studio 2012</code> folder in the <code>New Project</code> dialog. I am not sure if this will move in the future, but that is my gut feel. For now, if you are running VS 2013 Preview and you cannot find the HotTowel SPA template, refer to my image below to locate it.
<img src="http://www.johnpapa.net/wp-content/uploads/2013/09/2013-2012-mvc-600x302.png" alt="2013 2012 mvc" width="600" height="302" class="aligncenter size-large wp-image-20681" />

