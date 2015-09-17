---
layout: post
title: Build Apps with Angular and Breeze
date: 2013-10-26 23:05
author: John
comments: true
categories: [Uncategorized]
---
<img src="http://www.johnpapa.net/wp-content/uploads/2013/09/angular-icon.png" alt="angular-icon" width="96" height="96" class="alignleft size-full wp-image-21531" />You know how sometimes we start coding a simple app and you start sprinkling a few cool tiny features and suddenly you realize your app has blossomed into something special? Well, that's how I feel about the app you will build in my latest course-series (yes, "series" is no typo) for <a href="http://pluralsight.com" target="_blank">Pluralsight</a> titled "<a href="http://jpapa.me/spangz" target="_blank">Building Apps with Angular and Breeze</a>". I started out thinking I'd just help folks get up to speed on building simple Angular apps, but the app started to speak to me. It wanted to do more and when doing more the app needed some structure. Pretty soon patterns emerged as the story evolved. 

So let's talk about a cool Angular app, kick-starter NuGet packages, HotTowel, Breeze, and a new series of courses!

<h3>Experiencing the Story</h3>
Something I feel very strongly about was showing HOW the app evolved. It would be much easier for me to just show the app in its completed state and walk through the code. It would be a disservice though as you'd miss out on all of the decision points where I decided to refactor working code, why I refactored it, and what options I weighed, and how to refactor it. As we all know, that's real world development. Of course, this meant the course took me much longer to complete than if I just walked through it (which is a fine teaching tool, but just not the one i wanted to choose here).  The net result is what I believe is a valuable experience where you get to join me for a story of how to build a web app with Angular, Breeze, and JavaScript patterns.

<blockquote>I would be remiss if I did not call out Ward Bell (<a href="http://breezejs.com" target="_blank">Breeze.js</a> master) who once again has provided a ton of input on this course and the app. In fact, several Breeze features came out of this course (ex: a validation directive). Thanks Ward for both your technical input and being a tremendous friend!
</blockquote>

<h3>The Story Continues</h3>
The added benefit of this is that I was able to craft a follow-up story quickly to this first course. The story will continue very soon in another course (Part 2 if you will in this course-series) where I expand on some more advanced topics including how to manage your app once you have a significant amount of real-world data interaction, saving and rehydrating from local storage, powerful data validation, and some surprises with some wicked cool ways to handle saving. :) The course is targeted to be out by Dec 31. And who knows ... perhaps if these are received well, i'll keep going :)

<a href="http://jpapa.me/spangz" target="_blank"><img src="http://www.johnpapa.net/wp-content/uploads/2013/10/10-26-2013-6-49-25-PM-600x77.png" alt="10-26-2013 6-49-25 PM" width="600" height="77" class="aligncenter size-large wp-image-22081" /></a>

<h3>What's Covered?</h3>
So what's in this course? Well, the description in a nutshell is that you will build a Single Page Application (SPA) from scratch using JavaScript, Angular, and Breeze. You will learn how to combine the Angular presentation framework, rich data features of Breeze, and raw features of JavaScript, CSS, and HTML5 to create robust modern web applications. There is a live demo so you can see what you are building, some starter code, step by step instructions, and some new NuGet packages to get you started (more on those later in this article).

The chapters/modules are below. I truly hope you enjoy this course as much as I enjoyed producing it!

<ul>
<li>Building an App with Angular, Breeze and JavaScript Patterns</li>
<li>Getting Started with Single Page Apps</li>	
<li>Angular from Scratch with HotTowel</li>	
<li>Creating Vertical Slice Through Your App</li>	
<li>Object Graphs, Extending Models, and Custom Directives</li>	
<li>Sharing Local and Remote Data Across Views</li>	
<li>Route Resolvers</li>
<li>Filtering</li>
<li>Paging, UI-Bootstrap, and Expanding the Data Service with Queries</li>
<li>Building a Dashboard</li>	
<li>Animations with Angular and CSS</li>
<li>Where Are We and a Look Ahead at What's Next</li>
</ul>

<h3>HotTowel Angular on NuGet</h3>
Sometimes you just want a kick-start ... or if you are like me, a kick in the pants to get your project off the "blank canvas". if that's you, then <a href="https://www.nuget.org/packages/HotTowel.Angular/2.0.0-rc3" target="_blank">HotTowel.Angular</a> is perfect for you. It uses some styling, some popular libraries, and of course Angular to get you off to a nice starting point. When its time to pull in Breeze, just ad in <a href="https://www.nuget.org/packages/HotTowel.Angular.Breeze/2.0.0-rc3" target="_blank">HotTowel.Angular.Breeze</a>. 

<pre class="prettyprint">
Install-Package HotTowel.Angular -pre
Install-Package HotTowel.Angular.Breeze -pre
</pre>

Notice that these are both pre-releases. That's because they depend on the package AngularJs.Core which is a package that uses the pre-release of Angular 1.2.0 RC3 (currently the latest). Once Angular goes live (which i hear is very soon) these packages will all no longer need the <code>-pre</code> option.

What's AngularJs.Core? This package makes it easy to grab just the core module for Angular. Angular 1.2.x begins a new era with Angular where each module is broken out into its own files. This means you don't need to load code you are not using. but it also means you don;t have to pull down a bunch of files into your project that you won;t be using either. So the <a href="https://www.nuget.org/packages/AngularJS.Core" target="_blank">AngularJS.Core package</a> pulls just the core module. There are also a series of other packages for the Angular modules that I created and maintain with Scott Allen and Jeremy Likness. <a href="http://www.johnpapa.net/modular-angularjs-nuget-packages/" target="_blank">You can find all of these packages on NuGet or in this article here</a>.
