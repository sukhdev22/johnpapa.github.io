---
layout: post
title: Compare Durandal to Angular, Not Knockout to Angular
date: 2013-08-22 14:40
author: John
comments: true
categories: [angular, durandal, jquery, knockout, requirejs, SPA, Uncategorized]
---
Odds are you have been asked recently: "How does <a href="http://www.knockoutjs.com" target="_blank">KnockoutJS </a>compare to <a href="http://www.angularjs.org" target="_blank">AngularJS</a>?" There seems to be a lot of attempts to compare these two awesome libraries. We can certainly compare them, but will this really get you where you want to go? 

If you hear this question, ask "why" the person is asking it. If s/he wants a JavaScript/HTML based presentation framework then suggest that you compare <a href="http://durandaljs.com/" target="_blank">Durandal</a> to Angular. Why? Because Knockout is at heart a data-binding library, while Angular and Durandal are presentation frameworks. This is a hugely important concept to grasp, so let's break down what's at the heart of these questions and how Knockout, Durandal and Angular approach them. But let's be clear: <strong>Knockout rocks. Durandal rocks. Angular rocks.</strong>

Below is a snapshot of the libraries that each uses.
<img src="http://www.johnpapa.net/wp-content/uploads/2013/08/ng-d-600x280.png" alt="ng-d" width="600" height="280" class="aligncenter size-large wp-image-20011" />

<h2>Under the Covers</h2>
Angular uses <a href="http://api.jquery.com/" target="_blank">jQuery</a> if present and falls back to its own <a href="http://docs.angularjs.org/api/angular.element" target="_blank">jqLite</a> otherwise. Durandal uses Knockout for data binding, RequireJS for dependency management, and jQuery (tho I can see this dwindling to a jqLite type presence in the future). They both uses promises too, which is a good thing! 
<blockquote>If you want to discuss and compare Angular and Durandal as SPA presentation frameworks, check out my upcoming <a href="https://www.anglebrackets.org/workshops.aspx" target="_blank">full day workshop and sessions at AngleBrackets and DevIntersections</a> October 27-30, 2013. <a href="https://www.anglebrackets.org/register.aspx" target="_blank">Register with code <strongPAPA</strong> to get a $50 discount too!</a> Douglass Crockford, Scott Guthrie, Scott Hanselman and Dan Wahlin will all be there too.
</blockquote>

<h2>Data Binding</h2>
Knockout does data binding very very well. Angular does data binding very well too, but it also does routing, animations, view orchestration, and more. Most people who dive into Knockout and Angular get this far and understand that. But the next step is understanding "why" Knockout doesn't do more. This is because Knockout is a data binding library. It's not a SPA framework.

My <a href="http://jpapa.me/spaps" target="_blank">Pluralsight course on building a SPA</a> uses Knockout extensively, but it also uses many other libraries to handle aspects that were essential to the app I built. I used Sammy for routing, RequireJS for dependency injection, jQuery for http calls, and so on. I used those libraries because they do their "thing" very well, just like Knockout does its "thing" very well. And they all work together very well. Durandal and Angular strive to do data binding + more (we'll get to those soon).

With Knockout we can data bind like this:

<pre class="prettyprint">
// JavaScript
var vm = {
    firstName = ko.observable('John')
};
ko.applyBindings(vm);
</pre>

<pre class="prettyprint">
<!-- HTML -->
<input data-bind="value:firstName"/>
</pre>
With Angular we data-bind like this.
<pre class="prettyprint">
// JavaScript
// Inside of a personController
this.firstName = 'John';
</pre>
And the Angular HTML markup using the new "Controller As" syntax which I prefer over <code>$scope.firstName</code>.
<pre class="prettyprint">
<!-- HTML -->
<div ng-controller="personController as vm">
    <input ng-model="vm.firstName"/>
</div>
</pre>
There are syntax differences, but data binding is quite simple either way.

<h2>Those Darn Parenthesis!</h2>
You can't talk about Knockout and Angular without addressing the "parenthesis" issue. So let's take a quick diversion here.

Angular handles data binding using a dirty checking strategy via watches and its digest cycle. What may mean more to you is that Angular allows you to bind to Plain Old JavaScript Objects (POJO) with two-way binding and changes will propagate to all binding instances of that property. If you want this with Knockout then you will be using ko.observable(), which uses the observer pattern to notify all bindings and sources when the properties change. The implementations are very different, but both are effective. 

So why do you care? Because with Knockout that means you often have to use parenthesis to unwrap your observables to get to their values. Notice the HTML below and its parenthesis in the HTML.
<pre class="prettyprint">
<input data-bind="value:customer().contactPerson().firstName"/>
</pre>

This can be a pain point and is one of the reasons folks lean to Angular. However, Knockout and Durandal 2.x have plug-ins/modules that will remove the parenthesis issue (for ES5 supported browsers). That is a topic for which I will blog about later, but for now <a href="http://durandaljs.com/documentation/Binding-Plain-Javascript-Objects/" target="_blank">read more here</a>. This will allow you to do this with Knockout/Durandal.
<pre class="prettyprint">
<input data-bind="value:customer.contactPerson.firstName"/>
</pre>
Which is much more comparable to Angular.
<pre class="prettyprint">
<input ng-model="customer.contactPerson.firstName"/>
</pre>

<h2>Why Durandal and not Knockout?</h2>
So let's get back to the question of which one (of Knockout and Angular) to use for a SPA. Knockout is just data binding, so if you want more than that, you could just use Angular. Or, you could look at Durandal and Angular. Why Durandal? Because it is a presentation framework on the same level as Angular. They solve the same problems (in different ways of course). They both have routing, animations, view orchestration, dependency management, as well as data binding. 

Durandal is a natural progression from Knockout because Durandal uses Knockout. In fact, Knockout is baked throughout Durandal. Durandal uses Knockout for data binding because its solid, very widespread, and reliable. Angular rolled their own data binding. 

<h2>What Have We Learned?</h2>
The comparison of Knockout to Angular is apples to oranges. Well, maybe more like comparing the engine of a Ferrari to an entire Lamborghini. The both do data binding, but Angular strives to do more (presentation framework) while Knockout strives to do data binding only. There are offshoots of data binding features too. For example, Angular has directives (commonly for attributes and elements) and Knockout allows you create binding handlers (for inside the data-bind) or even binding providers (create your own attributes/elements).  My point here is that data binding is powerful and both of these fine gentlemen realize that and take advantage of it. However, Angular goes further. This is where Durandal steps in and builds on top of Knockout. 

So the next time you are asked about Knockout or Angular for a presentation framework, redirect the question to Durandal and Angular.
