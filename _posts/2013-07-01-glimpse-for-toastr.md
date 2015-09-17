---
layout: post
title: Glimpse Extension for Toastr
date: 2013-07-01 12:28
author: John
comments: true
categories: [glimpse, toastr, Uncategorized]
---
Glimpse.Toastr, a plugin for integrating toastr diagnostics into Glimpse, is now available on <a href="https://nuget.org/packages/glimpse.toastr" target="_blank">NuGet</a> and <a href="https://github.com/johnpapa/glimpse.toastr" target="_blank">GitHub</a>.

If you haven't checked out <a href="http://getglimpse.com/" target="_blank">Glimpse</a> yet, you are missing out. And if you haven't checked it out recently, then definitely go grab the latest as its new Heads Up Display (HUD) is nothing but awesome-sauce! At a glance it gives you a ton of information to help debug your app. What makes Glimpse stand out is that it works in any browser (it's not a browser plug-in), shows server or client information, and is constantly being improved.

<img src="http://www.johnpapa.net/wp-content/uploads/2013/07/glimpse1-600x185.png" alt="Glimpse HUD" width="600" height="185" class="aligncenter size-large wp-image-19001" />

<h3>Glimpse Heads Up Display</h3>
In its passive state, Glimpse's HUD is a toolbar at the bottom of the page that updates dynamically as you interact with your app. It shows you some interesting stats based on the extensions that you enabled. The image above shows the request times for the page to load over HTTP, Ajax calls, and the controllers that fired. It's active state is enabled when you roll over a specific area. This causes a panel to appear with even more detailed information.

Glimpse is billed as "the server information you need, where you want it". It is a fantastic tool that provides quick insight into what is going on in your application from the browser. Glimpse has a core library and from there you can add <a href="http://getglimpse.com/Packages" target="_blank">different extensions</a> to help shed light on server features such as Entity Framework, Ninject, ASP.NET MVC, Newtonsoft Json and more. However, Glimpse can do more than just show you server information in the browser.

<h3>Glimpse.Toastr</h3>
Glimpse extensions rely on a core library that uses a glimpse.axd file in your web app. This is what helps drive the core server side functionality from the server. Then on the client there is a glimpse.js file that helps render the HUD in the browser. I wanted to disconnect the server and try to just use the client piece, so I could use Glimpse on any server to help shed light on client side code. Basically, skip the glimpse.axd on the server and just use glimpse.js with an extension. 

<img src="https://a248.e.akamai.net/camo.github.com/77b541f588180768927d92ac8e6c2a1870edb895/687474703a2f2f6a6f686e706170612e6e65742f77702d636f6e74656e742f696d616765732f676c696d7073652e746f617374722e706e67" width="1289" height="331" class="aligncenter" />

I contacted the creators of Glimpse, <a href="https://twitter.com/nikmd23" target="_blank">Nik Molnar</a> and <a href="https://twitter.com/anthony_vdh" target="_blank">Anthony Vander hoorn</a>, and asked them for some help in getting jump-started with this. Luckily they had already begun thinking about this and it was relatively simple to get going. This is how I started writing the Glimpse extension for <a href="https://github.com/CodeSeven/toastr" target="_blank">Toastr</a>. In a future post I'll dive more into how I created this extension so you can see how you can create your own extensions.

Glimpse.Toastr shows you information about the life-cycle of each toast. When it was shown/hidden, the type of toast, each toast's configured options, toastr-wide options, and how long each toast lasted (see image above).

<h3>Installing via NuGet</h3>
You can install glimpse.toastr using NuGet by using the command <code>install-package glimpse.toastr -pre</code>. It is currently in pre-release as I am hoping to gather some feedback and work out any kinks. 

<h3>What's Next?</h3>
Glimpse.Toastr is not currently in the HUD, but I am exploring how to add a small panel in the HUD for it. I'd also like to see the Glimpse team make the glimpse.js file be part of its own NuGet package so I can just pull in that one file. Currently there is a Glimpse core package that has the glimpse.js and the server components such as glimpse.axd. I can;t use that since it would put code on the server, which glimpse.toastr does not need. So for now I embedded the glimpse.js file directly into glimpse.toastr. But the right way to do this is to have it rely on a glimpse client core package.
