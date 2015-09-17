---
layout: post
title: HotTowel.Angular and ASP.NET Web API 2 Compat
date: 2013-11-16 15:49
author: John
comments: true
categories: [Uncategorized]
---
If you watched my course <a href="http://jpapa.me/spangz" target="_blank">Build Apps with Angular and Breeze</a> the first week it was out and followed along by installing HotTowel, you may have hit an incompatibility with the recently released ASP.NET Web API 2 and Entity Framework 6. Good news! The exercise files, <a href="https://github.com/johnpapa/Pluralsight-CC-Angular-Breeze-Extra" target="_blank">github repo code samples</a>, and the NuGet packages for HotTowel.Angular and HotTowel.Angular.Breeze have all been updated to work with Breeze 1.4.5, Web API 2, and Entity Framework 6. So as you go through the course you can use the latest and greatest now. This course came out right when these new technologies went live, but it is all compatible now, so please enjoy the course and thanks for watching!

2 new videos clips for HotTowel installation have been provided to Pluralsight and are being uploaded. The new video shows all you need is:

<pre class="prettyprint">
// install Sql Server Compact, for the database support
install-Package EntityFramework.SqlServerCompact

// Install HotTowel (angular, breeze, asp.net web api, etc)
Install-Package HotTowel.Angular.Breeze
</pre>

You no longer need the <code>pre</code> as Angular 1.2.1 is now fully released.

Hope this helps!

<em>Note</em>: If you have older versions of EF, ASP.NET Web API 1, or EF <= 5 then you may want to remove those first. There are compat issues when mixing those with the newer ones. If you simply try putting HotTowel on top of those, it likely won;t work. So clean it out first.


