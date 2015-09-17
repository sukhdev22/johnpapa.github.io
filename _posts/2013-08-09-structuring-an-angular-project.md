---
layout: post
title: Structuring an Angular Project
date: 2013-08-09 21:01
author: John
comments: true
categories: [angular, breeze, knockout, SPA, Uncategorized]
---
<p><img src="http://www.johnpapa.net/wp-content/uploads/2013/08/ngapp-245x600.png" alt="ngapp" width="245" height="600" class="alignright size-large wp-image-19501" />We can build amazing SPA and HTML5 applications when choosing a powerful framework like <a href="http://www.angularjs.org" target="_blank">Angular</a>, <a href="http://www.durandaljs.com" target="_blank">Durandal</a>, <a href="http://emberjs.com/" target="_blank">Ember</a>, or <a href="http://backbonejs.org/" target="_blank">Backbone</a>. And while I love <em>my personal favorites Angular and Durandal</em>, it's not all magic. There is a learning curve and some things are helpful to decide up front. Once you choose your presentation framework, you should decide how you will organize the structure of your project.</p>

<blockquote><strong>UPDATE: </strong>Learn how you can <a href="http://www.johnpapa.net/angular-growth-structure/" target="_blank">refactor your Angular structure for growth in my "sequel" post.</a>
</blockquote>

<p>In this post I'll show one way how I organize my Angular based projects and discuss why I like it.</p>

<p>Before you ask "Why didn't he mention <a href="http://www.knockoutjs.com" target="_blank">Knockout.js</a>? Doesn't he love it anymore?", let me answer that up front. Knockout.js is awesome. I love it. I use it. In fact, it is an integral piece of Durandal such that I often refer to Durandal as Durandal/Knockout. But that is the point: Durandal and Angular are frameworks. Frameworks handle a lot of things for you that cover most of the plumbing you need in a SPA. Knockout handles 1 thing: data binding. Now, it handles it very well and has some awesome features that crop out of it, like custom binding handlers and extensions. But I do not consider Knockout a complete framework, nor do I believe it is intended to be one. So you'll often hear me talk about Durandal and Knockout together as a framework choice.</p>

<blockquote>
  <p>If you are interested in SPA, HTML5, Angular, BreezeJS or JavaScript patterns then you will love my upcoming course at <a href="http://pluralsight.com/training/Authors/Details/john-papa" target="_blank">Pluralsight</a>, due out in September 2013. Or if you prefer Knockout and Durandal check out <a href="http://pluralsight.com/training/Authors/Details/john-papa" target="_blank">my courses on Pluralsight today</a>.</p>
</blockquote>

<h2>Sorting Boxes</h2>

<p>Most of my client code ends up in one of these 4 folders. I like to keep code I wrote separate from code someone else wrote. Sounds pretty simple when you say that but I see a lot of projects where everything gets tossed in the same folder and it makes a mess to find what you need or run code analysis against just your code. (Who wants want to run static code analysis against angular or knockout?) I also want my tests separated from my app and all of my assets (images, fonts, css) in yet another folder.</p>

<pre class="prettyprint">/app
/content
/scripts
/test
</pre>

<p>So for me, all of my code goes in the <code>app</code> folder, 3rd party or vendor scripts go in the <code>scripts</code> folder, assets in the <code>content</code> folder, and tests in the <code>test</code> folder.</p>

<h2>App Code</h2>

<p>My <code>app</code> folder is where all of my files I wrote for my app reside. This includes JavaScript and HTML files. The root of the folder is where I put my app.js which is my boot file. This is where all the magic starts and the application gets kicked off. For angular this means the modules get loaded and run. I generally name my root module <code>app</code>. I also usually create a config.js here to store all of my commonly used variables across the app. For angular I store these in <code>app.value</code> or <code>app.constant</code>.</p>

<pre class="prettyprint">/app
    /controllers/
    /services/
    /views/
    /app.js
    /config.js
/content
/scripts
/test
</pre>

<h2>Controllers</h2>

<p>The <code>controllers</code> folder is where all of my controllers live. Makes sense, an app usually has several of them so why not put them all in one place. Notice what is not there though? The word "controller" in the name of the files. I'm not a fan of naming just for the sake of it. By putting all of my controllers in a <code>controllers</code> folder, guess what, I know they are controllers. I do not find an advantage in naming them "controller.session.js" or "sessionController.js". If you are wondering about the casing, I use camelCase because I it feels right :). That's just how I roll. When I use a controller, Angular creates a new one for each view instance. Should it be PascalCase ... that's your choice. It's more important to be consistent and understand that controllers come and go, and you can test this by tapping into the <code>$destroy</code> event.</p>

<h2>Services</h2>

<p>The <code>services</code> folder contains all of my services for the SPA. When I say services here I mean a unit of code that provides a discrete service to the rest of the app. I am not specifically talking about the Angular provider, service or factory, though these services may be constructed from those Angular features. I will generally have services for typical uses such as a logger, datacontext, routing, or storage. Sometimes I will add more specialized services here too such as work in progress or client side repositories. My services follow these 3 criteria: any set of code that can be ...</p>

<ul>
<li>reused</li>
<li>tested on its own</li>
<li>encapsulated </li>
</ul>

<p>I also put all of my directives in the <code>services</code> folder.</p>

<h4>Directives</h4>

<p>Generally I put them in a single file named <code>directives.js</code>. Some folks like to separate their directives, and I get it ... I just don't agree. I will often have several of these, but they are all small and often I want to look at other directives when I am developing new ones (for ideas). Now, I will create multiple files for directives if there is an obvious logical separation. For example, if I create a bunch of directives that apply just to using <a href="http://www.breezejs.com" target="_blank">BreezeJS</a> functionality, then sure, I'll make a file just for those. And what goes in a directive for me? Ideal candidates are any DOM interaction or events that are not covered by out of the box Angular directives. I also use this to wrap 3rd party widgets that I like. If I had a ton of directives and several files, then I would consider a new folder for them too. When I use filters, I also create a filters file in this folder. Some projects I don't use filters. Why? Well, that's a topic for another post.</p>

<h2>Views</h2>

<p>The final core folder is <code>views</code>, which is where my HTML resides. This includes inclusive views such as sessions.html. But it also includes partial views that may be inclusive or only intended to be used in another view. For example, some partial views have their own Angular controllers. These views can be placed in other views, and the controller comes with them. So they work anywhere. Then there are partial views that rely on some parent view. I tend to try to stick with the latter (views that have their own controller) ... that's just my preference. But I don't go nuts either way.</p>

<h2>Your Choice</h2>

<p>Ultimately how you organize your code is entirely up to you (and your team). I find it is immensely valuable to think it through before I start working with a team and tossing files all over the place. Having logical sorting boxes for all of your code just makes life easier. There are many ways to skin this cat so don't fret if you don't follow this exact pattern. That's what it is: a pattern. Not gospel.</p>

<h2>Next</h2>

<p>For smaller apps I find this structure quite simple, organizing by types. Once the app grows and starts expanding into multiple features and especially modules, I like to change the structure to group by feature. I'll explore this side by side a bit more in a future post. Both structures have value and really depend on how easy it is to find what you are looking for.</p>

<h2>Update</h2>

<p>In the comments Joel mentions a <a href="http://cliffmeyers.com/blog/2013/4/21/code-organization-angularjs-javascript" target="_blank">great post by Cliff Meyers</a> that discusses another approach to organizing an Angular app. Cliff's approach is to organize by functional area. There is much wisdom in this choice too. Where I differ personally is if the app is in a single module I consider the module the functional area. Then once within that area, I choose to separate by type as discussed above. For me, once I see a different functional features, I consider making a new Angular module and separating from there. But again, these depend on your comfort. Happy coding!</p>

