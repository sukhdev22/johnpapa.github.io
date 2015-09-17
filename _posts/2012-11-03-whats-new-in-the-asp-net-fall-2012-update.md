---
layout: post
title: What's New in the ASP.NET Fall 2012 Update?
date: 2012-11-03 17:11
author: John
comments: true
categories: [asp.net, azure, javascript, knockout, odata, signalr, SPA, Uncategorized, web api]
---
Last week at Build, <a href="https://twitter.com/shanselman" target="_blank">Scott Hanselsman</a> and <a href="https://twitter.com/jongalloway" target="_blank">Jon Galloway</a> presented a whirlwind tour of the new features coming to Visual Studio and ASP.NET. These features are meant to be additive to your experience as they will not impede any existing projects, but should help add more value moving forward. What's the goal? Once a quarter they release some yummy goodies for Visual Studio that you can run with.
<h2>Download it</h2>
You can grab the <a href="http://www.asp.net/vnext/overview/fall-2012-update/aspnet-fall-2012-update-release-notes" target="_blank">ASP.NET Fall 2012 Update BUILD Prelease </a>(gotta love those names at Microsoft) now and they mentioned that the official release (non preview) will be coming in December. <a href="http://www.asp.net/vnext/overview/fall-2012-update" target="_blank">Download link for it is on this page here</a>.
<h2>What's New?</h2>
<ul>
	<li>New SPA and Facebook templates</li>
	<li>Web API tracing (great for debugging)</li>
	<li>OData</li>
	<li>Hypermedia</li>
	<li>Windows Azure Authentication</li>
	<li>SignalR templates baked into VS</li>
	<li>New "Cafeteria Style" Single Page Application template (with Knockout baked in)</li>
</ul>
<h2>New Templates</h2>
<div>The tooling now has new templates for Single Page application and Facebook application.</div>
<a href="http://www.johnpapa.net/wp-content/uploads/2012/11/11-3-2012-9-16-42-AM1.png"><img class="aligncenter size-full wp-image-8401" title="ASP.NET Templates" src="http://www.johnpapa.net/wp-content/uploads/2012/11/11-3-2012-9-16-42-AM1.png" alt="" width="600" height="456" /></a>
<h2>Web API Tracing</h2>
<div>No longer are your Web API calls a mystical creature that is difficult to trace when something goes amiss. You can now see the tracing of your Web API calls in the debug window of Visual Studio. Very helpful to see what's actually happening as you run your apps and browse around. It does this with the SystemDiagnosticsTraceWriter class.</div>
<div> <a href="http://www.johnpapa.net/wp-content/uploads/2012/11/11-3-2012-9-22-11-AM1.png"><img class="aligncenter size-full wp-image-8391" title="Tracing" src="http://www.johnpapa.net/wp-content/uploads/2012/11/11-3-2012-9-22-11-AM1.png" alt="" width="600" height="258" /></a><a href="http://www.johnpapa.net/wp-content/uploads/2012/11/11-3-2012-9-16-42-AM1.png">
</a></div>
<h2>OData</h2>
<div>Adding [Queryable] to your controller methods will add some OData features out of the box. So if you add that attribute, you can simply change your url to api/values/$top=5. The response can whip out some very tight JSON, too.</div>
<h2>Hypermedia</h2>
<div>The returning JSON also adds in a small link to the next 5 records (this is baked into the JSON response). You can use the OData querystring to get the "next x" records or you can use a special method they expose in the results called __next (that is underscore underscore next) like this:</div>
<pre class="prettyprint">data.__next</pre>
<h2><a href="http://www.johnpapa.net/wp-content/uploads/2012/11/next-page.png"><img class="aligncenter size-full wp-image-8441" title="next page" src="http://www.johnpapa.net/wp-content/uploads/2012/11/next-page.png" alt="" width="600" height="199" /></a></h2>
<h2>Windows Azure Authentication</h2>
<div>You can publish your app to an Azure web site and add have your authentication process in place out of the gates. More from the ASP.NET web site:</div>
<blockquote>
<div>Windows Azure Authentication makes it simple to enable authentication for web applications hosted on Windows Azure using Windows Azure Active Directory. You can authenticate Office365 users, corporate accounts synced from on-premise Active Directory or users created in your own custom Windows Azure Active Directory domain.</div></blockquote>
<h2>SignalR</h2>
<div>Damien Edwards and David Fowler introduced us to <a href="https://github.com/SignalR/SignalR" target="_blank">SignalR</a> and now its been folded into the ASP.NET portfolio. There is a new file template in Visual Studio called the SignalR Hub class .</div>
<div><a href="http://www.johnpapa.net/wp-content/uploads/2012/11/11-3-2012-9-59-06-AM.png"><img class="aligncenter size-full wp-image-8451" title="signalR hub class template" src="http://www.johnpapa.net/wp-content/uploads/2012/11/11-3-2012-9-59-06-AM.png" alt="" width="600" height="276" /></a></div>
<div></div>
<h2>Facebook Auth and Apps</h2>
<div>They've added a new Facebook C# SDK NuGet package that makes it much simpler to access Facebook auth. So what can you do? You can add the Facebook Authorize attribute to a controller action so it will bounce you over to Facebook's auth and request specific types of permissions/access (like email, friends, etc).  You can also grab a Facebook user and bind it to a local class and gain access to Facebook apps.</div>
<div><a href="http://www.johnpapa.net/wp-content/uploads/2012/11/facebook.png"><img class="aligncenter size-full wp-image-8481" title="facebook" src="http://www.johnpapa.net/wp-content/uploads/2012/11/facebook.png" alt="" width="600" height="296" /></a></div>
<h2>Single Page Application</h2>
<div>The original template for Single Page Apps (SPA) made an appearance over a year ago in a preview and was later removed prior to VS 2012 being released. The first run at this template wasn't really a template, but rather a specific way to create a SPA. This new template is a template . Kudos to <a href="https://twitter.com/mkristensen" target="_blank">Mads Kristensen</a> for spearheading this at Microsoft. So what's here? It's a template that gets you started with the intent of helping you avoid the "blank page" syndrome and instead having a starting point for creating a SPA. Where you take it from there is up to you. This is especially important since there are many good ways to create a SPA. Here is their token ToDo demo which uses the template to start a ToDo app using Web API, MVC, jQuery, and Knockout:</div>
<div><a href="http://www.johnpapa.net/wp-content/uploads/2012/11/spa-demo.png"><img class="aligncenter size-full wp-image-8491" title="spa demo" src="http://www.johnpapa.net/wp-content/uploads/2012/11/spa-demo.png" alt="" width="600" height="340" /></a></div>
<div>The key takeaway here is not to model your SPA exactly how this template and demo do it, but rather to use it as a starting point to get you going. Scott H calls it a cafeteria plan, where you can choose what you want. I agree with that assessment too.  It starts you out with ASP.NET MVC, ASP.NET Web API, <a href="http://knockoutjs.com" target="_blank">Knockout.js</a>, jQuery, modernizr, and some starter modules to get you going with SPA work. I dissect this a bit more in my post <a href="http://johnpapa.net/insidespatemplate" target="_blank">Inside the New Single Page Apps Template</a>.</div>
