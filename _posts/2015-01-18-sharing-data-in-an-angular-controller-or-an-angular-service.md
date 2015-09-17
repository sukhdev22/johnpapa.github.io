---
layout: post
title: Sharing Data in an Angular Controller or an Angular Service
date: 2015-01-18 23:36
author: John
comments: true
categories: [angular, breeze, javascript, Uncategorized]
---
I received a great question about model data recently. A question I hear a lot that is about an extremely common situation that most Angular developers will face. The reason I think it comes up is that there are many examples showing different ways to code the situation, none of which are wrong, and none of which are absolutely right.

I found myself typing up the answer and realized that this is a great opportunity to share the thought process on how I think about these situations. You may agree with my conclusion, or you may disagree, and that's cool. We'll still be friends :) But I think what's most important is to walk along the thought process so you can decide for yourself.

<h2>Sharing Data Among Controllers</h2>

Here is the question I received (in paraphrased format to shorten it)

<blockquote>
  Imagine we have a controller for the list of items. The Controller gets its data from some source such as a route's <code>resolve</code>. Where should I store the data? Is it architecturally correct to store it in the service right after the controller has been initialized and clean up the service in <code>$on('destroy')</code> callback? Or should I store the data in the $scope, for example, and call the service for saving/getting the data?
</blockquote>

Laying out the situation, I imagine a route that has a resolve function that might call a <code>customerService.getCustomers</code>. This resolve could then inject its results into a <code>CustomersController</code>. Once in the controller, the data can be filtered, edited, or whatever. Then when the data changes, do we send that changed data back to a service, maybe even the same service <code>customerService</code>, and have it make the <code>$http</code> calls to update it on the back-end?

Or another options the author lays out is keeping the data in a service where it can be shared. This type of service acts as a client side model. This scenario might have the resolve get the data from <code>customerService</code>, then add it to a client side model <code>customersModel</code>, and then inject the model into the <code>CustomersController</code>. This allows the controller to manipulate the data in a Singleton service that can be shared among controllers.

The author goes on to outline the differing opinions on his team ...

<blockquote>
  "in my opinion, the second variant doesn't allow to share (read or edit) the data from other controllers. However, my colleague's opinion is that service should be stateless, more like $http. What do you think on this matter?
</blockquote>

What do I think? I think you are both right. Your colleagues say services like <code>$http</code> should be stateless. Yes, absolutely services can be stateless and if they are built that way. But services can also act as models with state and there is absolutely nothing wrong with that.

<h2>Whittling it Down</h2>

OK, there are 3 scenarios I mentioned here:

<ol>
<li>Controller hosts the model, <code>customerService</code> just gets and saves, no sharing between controllers</li>
<li><code>customerService</code> service gets the data and hosts the data, many controllers manipulate it</li>
<li><code>customerService</code> gets the data, another <code>customersModel</code> hosts the model, and a controller manipulates it</li>
</ol>

<h3>Controller is the Owner</h3>

The first option works fine and is pretty good for many simple scenarios. Simple isn't bad, it just means you don't need to share the data across multiple controllers. You can still share between controllers and sub controllers and directives via <code>$scope</code>. If you are fine with going and getting the data and being stateless, this is a good option. I've written a lot of code like this and it's ideal for get the data, manipulate the data, save the data ... next!

<h3>Service is a Model and a Service</h3>

This pattern has been used a lot of places. An object takes on the role of both getting/sending data and hosting the model for the data. I'm not personally a fan of this pattern, but it is an oft used pattern. I don't like mixing these concerns, but it does work and you won't be thrown into jail by the Angular police. If you go here, it works, and you can share the service between multiple controllers.

<h3>Model Service and a Separate Action Service</h3>

I'd rather have 2 services. I like one service that gets and sends the data (handles the verbs) and one service that acts as the model (the nouns). This allows for more re-use, more clarity, and frankly just feels better to me. This is the pattern I used in my <a href="http://www.pluralsight.com/courses/build-apps-angular-breeze-part2">Angular and Breeze courses on Pluralsight</a> where I wanted to share the data across multiple controllers. Once I get customers, I want all of the Views to have access to those customers without hitting the server again. I have the choice to refresh, but I wanted to cache them in a local service. This allowed me to change in one place and the changes are seen in all controllers that shared the model.

<h2>Summary</h2>

It is worth pointing out that whenever you cache data and hold state you need to consider when to refresh that state. It's not hard, but you need consider which types of data you want to cache and which you do not want to cache. Anything that is volatile, like inventories, you may not want to hold state on. However, lists of customers or states or stores are less volatile and could be hosted in state. Either way, I don't let this bother me in my choice, I just make sure I handle the state properly and refresh when needed.

Ultimately the best answer is to consider the options and weigh them for your app's needs. I hope this helps get you there.

What would I do? I would not make a service that is a model and a service. That's just not my style. I would start with making a service get the data and have the controller manipulate it. If I had need of sharing the data, I'd consider making a model and going to the 3rd option I mentioned. If I had a need to share data and create a model, I likely would have need for a rich model and that's where model validation and dirty checking could play a factor too. That's when i'd go even further and add in Breeze.

But in short, start with the simplest: service gets data and gives it to a controller. Then move to a model based solution when you need sharing.
