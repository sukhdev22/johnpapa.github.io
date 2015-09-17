---
layout: post
title: The Angular Team on Angular 1.3 and the Road Ahead to Angular 2.0
date: 2014-11-13 20:02
author: John
comments: true
categories: [adventuresinangular, aia, angular, javascript, Uncategorized]
---
<p><a href="http://adventuresinangular.com"><img src="http://www.johnpapa.net/wp-content/uploads/2014/08/AiA-logo-sm.png" alt="AiA logo - sm" width="100" height="101" class="alignleft size-full wp-image-32351" /></a> We had the pleasure of meeting with the AngularJS team to discuss the recent release of 1.3 and their plans for 2.0 on this <a href="http://jpapa.me/AiA-016">week's episode of Adventures in Angular</a>. Join us and <a href="https://twitter.com/bradleygreen">Igor</a>, <a href="https://www.youtube.com/watch?v=ojMy6m_fcxc">Brad</a>, <a href="https://twitter.com/briantford">Brian</a>, and <a href="https://twitter.com/mhevery">Misko</a> (the father of Angular) for this longer episode as we dive into their strategy. You can also read the transcripts on our site.</p>

<h2>Features</h2>

<p>Here are some of the top features available in Angular 1.3.</p>

<ul>
<li>angular-hint</li>
<li>bindToController</li>
<li>One-Time binding</li>
<li><a href="https://docs.angularjs.org/guide/production">Disabling debugging</a></li>
<li>$httpProvider.useApplyAsync(true)</li>
<li>ngAria</li>
<li>ngMessages</li>
<li>ngModelOptions 

<ul>
<li>$rollbackView</li>
<li>allowInvalid</li>
<li>debounce</li>
</ul></li>
<li>ngStrictDi</li>
<li>Performance enhancements</li>
<li>$q Constructor</li>
</ul>

<p>You can try some of these in my demo application <a href="http://github.com/ng-demos">1&#46;3 Playground on github</a>. I'll be adding more soon. Be sure to check out this video by Brian Ford and Jeff Cross at <a href="https://www.youtube.com/watch?v=ojMy6m_fcxc">ngEurope on what's new in Angular 1.3</a>, too.</p>

<h2>Nutshell</h2>

<p>Angular has been around for 5 years and the web has changed. Massively. Angular is great, its adoption has been astronomic, and 1.3 has some fantastic new features, especially the performance improvements you get out of the box. But in my opinion it needs to evolve to ES6 and the future of the web (web components, shadow DOM, etc) to continue to be the amazingly productive tool in the future that it is today. Changes will come, some in the form of different syntax, but the soul of Angular must remain the same. Testable. Low boilerplate. Separation of concerns. Data binding. Low friction. I can learn syntax and tools will evolve to adapt to that (tooling is always close behind tech).</p>

<p>There also must be a migration story. The team has shared that they are aware of this and will help shape that story. I am contributing time to this effort myself.</p>

<h2>Questions ?</h2>

<p>There has been a lot of confusion, concern, and questions about what Angular 2 will be like and how the migration path may evolve. We tried to address many of these questions on the interview with the Angular team, to let them answer these directly. We also answered some questions from twitter that were posted while we recorded the show (thanks everyone!). Here are some we received from the community and my interpretation of them:</p>

<p><strong>Q.</strong> Regarding ‪#AngularJS2 what are the new benefits of 2.0? Is 3 way data binding going to be a built in functionality with AngularJS 2.0?</p>

<p><strong>A.</strong> Interesting question and I assume this is in regards to the recent news about Google and <a href="http://www.firebase.com">Firebase</a> (which offers 3-way binding). I don't know the answer to this and there has been little talk about what will come of their joining. But I am guessing that Firebase will remain separate and 3-way binding will continue to be an add-on.</p>

<p><strong>Q.</strong> Is it recommended that apps built with AngularJS 2.0 use AtScript for the benefits of improved tooling support?</p>

<p><strong>A.</strong> AtScript is optional. We spent a good amount of time on this topic with Misko (and in an upcoming pod cast in next week's episode) as it seems to be on everyone's minds. The team has said AtScript is optional, but it will help enhance the experience, and be usable for JavaScript (not just for Angular). My personal hope is that it gets merged with <a href="http://typescriptlang.org">TypeScript</a>.</p>

<p><strong>Q.</strong> When might we expect any content to be released on Angular 2.0 and migration from 1.3 -> 2.0? What are those breaking changes that we now have to look out for when going through Angular 1.3 courses?</p>

<p><strong>A.</strong> Fantastic questions. Angular 2.0 is still early and I am told content will be released as it progresses. The router is pretty far along and will be worked back into Angular 1.x, promises the Angular team. Breaking changes are unclear yet as Angular 2.0 is not yet feature complete, and thus features and a migration path have not yet materialized. I am personally very interested in the migration path (documentation, guidance, and hopefully some tooling) and I plan to write as much about this as I can, when the team gets closer. This is an important area. For now you can follow "controller as", ES6, and other concepts that bring us closer to what they have revealed. You can also refer to my <a href="http://jpapa.me/ngstyles">Angular Style Guide</a>, which I am evolving with the Angular team to help provide consistency to 1.x apps which will make it easier to have a migration path. Igor has personally spent a lot of time helping me refine it, and I truly appreciate it as the community will benefit from his insight.</p>

<p><strong>Q.</strong> We are planning to use AngularJS, but most of our web applications are developed on top of ASP.NET MVC with razor view engine. What is the best approach for us to migrate to AngularJS? Combine the MVC and AngularJS?</p>

<p><strong>A.</strong> Any back end works with Angular, that's the beauty of it and SPA. The simplest setup is an architecture with a lightweight Web API server such as node.js or ASP.NET's project k (vNext), though today's ASP.NET Web API is a fine choice in preparation for vNext. I recommend learning Gulp and Bower for a build process and package management too. Whether you choose node or ASP.NET you'll be happy you made that choice. Especially since Visual Studio's recent announcements have also revealed a lot of features for these extremely popular tools. I'll do a future post on this architecture if there is interest.</p>

<p><strong>Q.</strong> I saw the RIP slides on-line for some Angular features. Are they really going away?</p>

<p><strong>A</strong> I am sure in hindsight the team would have presented this better. We hit on these topics explicitly and in detail with the Angular team in this episode due to the ways this was miscommunicated (in my opinion). In short the 5 items are simply being replaced. $scope will be replaced with another means to handle data, angular modules will be replaced with ES6 modules, the DDO (directive definition object) has always been a pain and will be simplified greatly (very different from what they say), jqLite is replaced with straight up JavaScript for the DOM (you can still use jQuery if you want to), and the many types of things you can create (controllers, directives, services, factories, providers, and so on) will use a more ES6 friendly and simplified syntax with classes. Listen for details from the team in this episode.</p>

<h2>Adventures in Angular</h2>

<ul>
<li><a href="http://adventuresinangular.com">Adventures in Angular web page</a></li>
<li>follow the show <a href="https://twitter.com/angularpodcast">twitter</a></li>
<li>listen to us on <a href="https://itunes.apple.com/us/podcast/adventures-in-angular/id907361052">iTunes</a></li>
</ul>

<p>Every Thursday morning you can join me and our All-Star panel of co-hosts <a href="https://twitter.com/josepheames">Joe Eames</a>, <a href="https://twitter.com/js_dev">Aaron Frost</a>, <a href="https://twitter.com/cmaxw">Charles Max Wood</a>, <a href="https://twitter.com/simpulton">Lukas Ruebbelke</a>, <a href="https://twitter.com/briantford">Brian Ford</a>, <a href="https://twitter.com/mhevery">Misko Hevery</a> for the latest episode of Adventures in Angular. We will rotate through cranking up a topic amongst ourselves and inviting a special guest in the Angular community. Each episode is 30 minutes-ish.</p>

<h2>Related</h2>

<p>My good friends <a href="http://weblogs.asp.net/dwahlin/my-thoughts-on-angularjs-1-3-and-2-0">Dan Wahlin</a> and <a href="http://onehungrymind.com/10-things-consider-keeping-level-head-angularjs-2-0/">Lukas Ruebbelke</a> have written great posts on their thoughts about Angular 2.0 and the recent social chatter. I encourage you to read their posts too.</p>

