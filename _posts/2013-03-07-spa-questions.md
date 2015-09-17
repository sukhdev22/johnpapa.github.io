---
layout: post
title: SPA Questions
date: 2013-03-07 14:58
author: John
comments: true
categories: [faq, SPA, Uncategorized]
---
I'm taking my own advice here and responding to some frequently asked questions I receive on SPA on my blog. I get some of these a lot and it just makes sense that I aggregate them and share for discussion. The questions are all good and they cover a variety of experiences. Hopefully by sharing them, they will be of benefit to others.

I encourage you to also chime in with your comments if you have more to add or have other questions.

<h3>Q1: Is SPA the future web trend?</h3>
SPA has been around for years, but recently it has gained a lot of momentum. It is an emerging area, for sure. However, the reasons businesses are attracted to it usually come down to its 3 core aspects:
<ul><li>Reach</li>
<li>Reduced Round Tripping</li>
<li>Rich User Experience</li>
</ul>

I think the web trend is more accurately depicted by achieving these 3 R's.

<h3>Q2: How do you secure a Web APIs for a SPA?</h3>
Web API can certainly be secured and the good news is that some of the ASP.NET MVC / SPA templates demonstrate this. Specifically, check out the SPA template that comes with <a href="http://www.johnpapa.net/asp-net-spa-templates/" target="_blank">VS 2012.2 Update mentioned here</a>. There are a variety of ways to implement security, this is one. You can also implement security at the method level.
<pre class="prettyprint linenums">
    [Authorize]
    [ValidateHttpAntiForgeryToken]
    public class TodoController : ApiController
    {
        // Controller methods go here
    }
</pre>

The anti forgery attributes are also worth considering, if that suits you. Check out the SPA template and the <a href="http://www.asp.net/single-page-application/overview/templates/breezeknockout-template" target="_blank">Breeze SPA template</a> for more concrete details.

<h3>Q3: Can anyone query for any server-side data?</h3>
Only if you allow them to. If you have data that should not be queryable, don't make it queryable. Lock down sensitive data like you would in any app. Most samples and demos will show what you can do but making Web API methods IQueryable. There are huge benefits to making the data flexible like this, but when specific data should be locked down, absolutely do that. One way to limit data is to remove IQueryable and construct the exact query on the server. You can also use a specific RPC like action in your Web API.  Yet another way is to use IQueryable on a method, but have it return a projection of the data (return all fields and rows except the sensitive ones). The bottom line is that security is still important and is still placed on the developer's shoulders to follow the requirements.


<h3>Q4: Does SPA work only with a .NET back-end?</h3>
SPA works on the client, so it works with any web server technology. It works great with a .NET back end, and my preference is an ASP.NET back end. However you can absolutely use PHP, Java, Azure cloud service, or a node.js server (just a few examples). The key concept here is reach: SPA allows for a multitude of devices and client browsers regardless of the back end. You can hook to any of them and call web services through AJAX.

<h3>Q5: Which core libraries should I choose for SPA?</h3>
<a href="http://durandaljs.com" target="_blank">Durandal</a> with <a href="http://knockoutjs.com" target="_blank">Knockout</a>, <a href="http://angularjs.org/" target="_blank">Angular</a>, <a href="http://emberjs.com/" target="_blank">Ember</a>, and <a href="http://backbonejs.org/" target="_blank">Backbone</a> are just a few solid choices.The key is in picking one that suits you. I prefer Durandal with Knockout because I believe it is easy to follow, scales well, is easy to build on, doesn't try to do too much, and has a great data binding core (which I prefer). Angular is another library I like as it has similar qualities. If you have time, it is certainly worth looking into these and choosing your favorite. They all have pros and cons and very different styles. There are other choices too, like Batman or CanJS. 

The key is not to get hampered by choosing, but to choose one that fits for you, your project, your team, and allows you to build on it. You can always choose another one later for your next project :) 

<h3>Q6: Which core libraries do you recommend?</h3>
I prefer the combination of Durandal and Knockout along with some others like Breeze and toastr. If you install <a href="http://johnpapa.net/hottowel" target="_blank">HotTowel</a> you will get my core list of preferences.

<h3>Q7: Does Hot Towel work with ASP.NET (no MVC) ?</h3>
Yes, but you will want the NuGet package named HotTowelette. <a href="http://nuget.org/packages/hottowel" target="_blank">Hot Towel</a> is designed for ASP.NET MVC while <a href="http://nuget.org/packages/hottowelette" target="_blank">Hot Towelette</a> is designed for ASP.NET without MVC. The libraries and App JavaScript are the same in both. The only differences are in using MVC routing vs a startup HTML page. In fact, both use ASP.NET razor, web optimization, and Web API too.

<h3>Q8: How much data should be pushed to the client in a SPA?</h3>
These are the determining factors in how much data to send to the client in an initial page:
<ul><li>Data that will be displayed for that first page</li>
<li>Lookup list data for any drop downs on that page</li>
<li>Data that is required for and presentation rules</li>
</ul>
On a view that would show a list of recipes, I would get the recipes and some key factors to display (like recipe name, the dish, and other key info) that can be displayed in a list. Enough for the user to make a determination on what to pick. Then when the user dives into a recipe, then go get that 1 recipe's details.

The general rule is get what you user will almost certainly need up front. Then get other data as they request it.

<h3>Q9: Why doesn't Hot Towel include more examples?</h3>
It's the difference in my mind of a template and a sample. Hot Towel is a template to build on. A sample would include more example code (that would be ripped out later by you).

When I built the Hot Towel template I had a focus on providing enough to get folks going with the right tools, and just enough starter code to guide the way. I did not want anyone ripping out code. I'm not a fan of templates that start you down a path and make you remove tons of files and code and change direction. Those are samples.

Samples are good. In fact, samples can be excellent (like the other templates, which I feel are more like samples). Those serve another purpose: to show how you can do things.

Back to the Hot Towel template ...if I include code that uses Breeze, I would be tempted to add a datacontext.js and a model.js on the client. They would contain data access code and code to extend the models on the client. Then I would be tempted to add a controller, some server-side models, an ORM and a database. Once there, I'd want to use the data in multiple screens, which leads me to more Knockout and caching with Breeze. Then I might be tempted to add editing, which would lead to change tracking. Soon I have a full-blown app. Or more conservatively, I have a sample again. While these approaches would provide more guidance on how to put these together, they would not help you "get started" with a template where you can just start building and adding your own code. If I stop short of some of these features, it's still walking down a road that requires you to change how I did it.

As it stands today, Hot Towel is pretty darn close to a template in the truest sense. You create a new project and you are off and adding your own code.

You could argue (and you may be) that Breeze shouldn't be in there since I don't use it in the template. Nor do I use moment.js, BTW. However, I argue that they are both excellent libraries that I would not want to build a CRUD based SPA without them. 



