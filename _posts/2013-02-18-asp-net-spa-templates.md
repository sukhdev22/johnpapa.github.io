---
layout: post
title: ASP.NET SPA Templates Released
date: 2013-02-18 18:37
author: John
comments: true
categories: [asp.net, breeze, durandal, ember, hottowel, javascript, SPA, Uncategorized, visual studio 2012]
---
Today the ASP.NET team released the RTM version of the ASP.NET and Web Frameworks 2012.2. This includes updates for ASP.NET MVC, ASP.NET Web API, ASP.NET Web Pages, Web Optimization, SignalR, and the ASP.NET SPA Template. The <a href="http://jpapa.me/scottguaspnetwt" target="_blank">official announcement is on Scott Guthrie's blog</a>. 

I'll focus this post on the new SPA templates that accompany this release. 

<style>
tr {
    border-bottom: #e7e7e7 1px dotted;
}
thead {
    font-weight: bold;
}
table tr td:first-child {
    text-align: left;
}
table td {
    padding: 4px;
    text-align: center;
}
</style>

<h2>Comparing the Templates</h2>
I created a quick comparison chart of what's inside each template. All of them have value depending on where your interests lay. 
<table>
<thead>
<tr>
<td></td><td>ASP.NET SPA</td><td>Breeze</td><td>Ember</td><td>Durandal</td><td>Hot Towel</td>
</tr>
</thead>
<tbody>
<tr><td>Includes ToDo Sample</td><td>Yes</td><td>Yes</td><td>Yes</td><td></td><td></td></tr>
<tr><td>Includes Bare Template</td><td></td><td></td><td></td><td>Yes</td><td>Yes</td></tr>
<tr><td>Navigation and History</td><td></td><td></td><td>Yes</td><td>Yes</td><td>Yes</td></tr>
<tr><td>Uses Ember</td><td></td><td></td><td>Yes</td><td></td><td></td></tr>
<tr><td>Uses Knockout</td><td>Yes</td><td>Yes</td><td></td><td>Yes</td><td>Yes</td></tr>
<tr><td>Uses Breeze</td><td></td><td>Yes</td><td></td><td></td><td>Yes</td></tr>
<tr><td>Uses Durandal</td><td></td><td></td><td></td><td>Yes</td><td>Yes</td></tr>
<tr><td>Toastr, Moment, Twitter Bootstrap</td><td></td><td></td><td></td><td></td><td>Yes</td></tr>
</tbody>
</table>

<blockquote>I'll also be discussing the various templates in my upcoming (March 2013) <a href="http://www.pluralsight.com" target="_blank">Pluralsight </a>course titled "SPA Jump Start". This course is perfect for developers who want to know how to get started with SPA as I walk through creating a SPA from scratch to completion. This is a beginner level course that focuses on staying productive by leaning on some great libraries while my <a href="http://jpapa.me/spaps" target="_blank">intermediate level SPA course</a> shows how to create many of the features by hand. </blockquote>

<h2>ASP.NET SPA Template</h2>
The intent of this template is to provide a starting place and sample for building a basic SPA with 1 view. If you want to move on from here to provide other features such as multiple views and sharing of data across those views, you can do that by pulling in other libraries like Sammy.js or Breeze.js (or choose your own favorites). Once you understand the SPA fundamentals, you can move on to build your own SPA using this as a starter model or see Hot Towel for a jump-start.

<img src="http://www.johnpapa.net/wp-content/uploads/2013/02/2-17-2013-11-49-15-PM.png" alt="2-17-2013 11-49-15 PM" width="500" height="347" class="aligncenter size-full wp-image-15311" />

I previously described the ASP.NET SPA template in my post <a href="http://www.johnpapa.net/inside-the-asp-net-single-page-apps-template/" target="_blank">Inside the ASP.NET SPA Template</a> here. Only a few things have changed since then in this template since its RC in December 2012. They added camelCasing of the JavaScript variables, which are converted from PascalCase from the server. This is nice since that is a common convention. 

You will also find one of the helpers for the new Knockout binding features in Visual Studio, too. Look in the <code>todo.viewmodel.js</code> and you will find a special comment (shown below) that helps when you are trying to get intellisense inside a <code>foreach</code> binding on the <code>todoLists</code> member. 

<pre class="prettyprint linenums">
window.todoApp.todoListViewModel = (function (ko, datacontext) {
    /// <field name="todoLists" value="[new datacontext.todoList()]"></field>
    var todoLists = ko.observableArray(),

</pre>

This provides intellisense when inside a foreach binding.

<a href="http://www.johnpapa.net/asp-net-spa-templates/2-18-2013-12-09-28-am/" rel="attachment wp-att-15341"><img src="http://www.johnpapa.net/wp-content/uploads/2013/02/2-18-2013-12-09-28-AM-600x216.png" alt="2-18-2013 12-09-28 AM" width="600" height="216" class="aligncenter size-large wp-image-15341" /></a>

<h2>Hot Towel SPA Template</h2>

<blockquote>Hot Towel: Because you don't want to go to the SPA without one!</blockquote>

<a href="http://www.asp.net/single-page-application/overview/templates/hottowel-template" target="_blank">Download the VSIX for the Hot Towel SPA template here</a>

The Hot Towel SPA template is different from the other templates and makes use of a lot more JavaScript libraries, including Breeze, Durandal, Knockout, RequireJS and Twitter Bootstrap. It provides a more complete application from which you can build your own. There are more concepts to be aware of, but once you understand the nature of rich client and Single Page Applications, this template might just be what you are looking for. If you want to build a SPA but can't decide where to start, use Hot Towel and in seconds you'll have a SPA and all the tools you need to build on it! You can <a href=" http://www.johnpapa.net/hottowel" target="_blank">learn more about Hot Towel here</a>.



<img alt="" src="http://johnpapa.net/wp-content/images/HotTowelPreview.png" />

<h2>BreezeJS SPA Template</h2>
<a href="http://www.breezejs.com/" target="_blank">Breeze </a>is an open source library for managing rich data in a JavaScript client. It handles querying, caching, change tracking, validation and more. The BreezeJS SPA template extends the ASP.NET SPA template with Breeze, showing how easily you can build a Single Page Application with BreezeJS for data and KnockoutJS for binding. Breeze is also featured in the Hot Towel SPA template.

<a href="http://www.asp.net/single-page-application/overview/templates/breezeknockout-template" target="_blank">Download the VSIX for the Breeze SPA template here</a>

<h2>Durandal SPA Template</h2>
<a href="http://durandaljs.com/" target="_blank">Durandal </a>is a new open source JavaScript library for rich client application development. It focuses on providing an enjoyable and productive developer experience centered around simple conventions and standard patterns like MVC, MVP and MVVM. The Durandal template provides a bare-bones starting point for a typical navigation-style application architecture, ready for your own content and features. Durandal is also featured in the Hot Towel SPA template.

<a href="http://www.asp.net/single-page-application/overview/templates/durandaljs-template" target="_blank">Download the VSIX for the Durandal SPA template here</a>

<h2>EmberJS SPA Template</h2>
If you prefer using the <a href="http://emberjs.com/" target="_blank">Ember </a>JavaScript library, then try the new EmberJS SPA template. Ember is a powerful MVC JavaScript library that solves a wide array of challenges for building rich client applications. The Ember template is an implementation of the same Knockout SPA template shipped with ASP.NET and Web Tools 2012.2, but uses EmberJS and Handlebars templating.

<a href="http://www.asp.net/single-page-application/overview/templates/emberjs-template" target="_blank">Download the VSIX for the Ember SPA template here</a>

