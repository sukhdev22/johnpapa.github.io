---
layout: post
title: Knockout Intellisense in Visual Studio 2012
date: 2012-12-16 03:33
author: John
comments: true
categories: [asp.net, html5, javascript, knockout, SPA, Uncategorized, visual studio 2012]
---
If you enjoy developing with <a href="http://Knockoutjs.com" target="_blank">Knockout.js</a>, then you'll be glad to hear that support has been added for Knockout Intellisense in Visual Studio 2012! These features are pretty cool and will save me and other developers from senseless typos. Developers who are newer to Knockout.js will enjoy the intellisense as an easy way to quickly learn the available built-in bindings.



<blockquote>For this post I'll explore these new features by using the new SPA Template included in the same release. You can read more about the SPA Template in <a href="http://www.johnpapa.net/inside-the-asp-net-single-page-apps-template/" target="_blank">my post Inside the ASP.NET SPA Template</a>.
</blockquote>



<a href="http://www.johnpapa.net/knockout-intellisense-in-visual-studio-2012/x-2/" rel="attachment wp-att-11201"><img src="http://www.johnpapa.net/wp-content/uploads/2012/12/x1-600x115.png" alt="" title="x" width="600" height="115" class="aligncenter size-large wp-image-11201" /></a>


The ASP.NET and Visual Web Developer teams released the ASP.NET and Web Tools 2012.2 update (Release Candidate) last week. There were many features in this release that you can <a href="http://weblogs.asp.net/scottgu/archive/2012/12/14/announcing-the-asp-net-and-web-tools-2012-2-release-candidate.aspx" target="_blank">check them out in Scott Gu's post here</a>. In this post I'll focus on a tooling feature that adds Visual Studio 2012 editor support for Knockout IntelliSense.



<blockquote>Knockout.js is a popular data binding library that provides databinding between targets elements in HTML (Views) and source objects in JavaScript (ViewModels). You can learn more about Knockout at my Pluralsight course <a href="http://jpapa.me/komvvm" target="_blank">Building HTML5 and JavaScript Apps with MVVM and Knockout</a>.
<a href="http://jpapa.me/komvvm"><img alt="" src="http://www.johnpapa.net/wp-content/uploads/media/Windows-Live-Writer/7323e2fa09cf_145CD/image_3.png" title="Knockout Course" class="aligncenter" width="1026" height="205" /></a></blockquote>


With this release, when you are in the HTML editor you will see intellisense when you type in a data-bind attribute. The following features will appear:
<ul>
<li> <code>db</code> snippet for creating the data-bind attribute</li>
<li>Built in bindings (left side of : )</li>
<li>Custom binding handlers (left side of : )</li>
<li>View model members (right side of : )</li>
</ul>

<h2>data-bind</h2>
Typing <code>data-bind=""</code> inside of an HTML element can become quite monotonous. Not anymore though. One of the features in this update is a snippet that types it for you when you type <code>db</code> inside of a tag. Place your cursor in an opening HTML tag like this one (right after the first v in div):
<pre class="prettyprint">
<div></div>
</pre>
Then type <space>db<tab><tab> and get:
<pre class="prettyprint">
<div data-bind="Name: Value"></div>
</pre>

<h2>Built in Bindings</h2>
When type in a data-bind attribute you will see a list of the built in bindings that Knockout supports and any custom bindings that you created and are available in your context. If you don't see it you can hit CTRL-&lt;SPACE> and it should appear in a list. 

<a href="http://www.johnpapa.net/knockout-intellisense-in-visual-studio-2012/ko-intellisense/" rel="attachment wp-att-11051"><img src="http://www.johnpapa.net/wp-content/uploads/2012/12/ko-intellisense.png" alt="" title="ko intellisense" width="437" height="213" class="aligncenter size-full wp-image-11051" /></a>

<h2>Knockout Region Highlighting</h2>
By default you get a new "Knockout Region" that you can change the foreground and background color. This is the one thing I don't like, and I changed my examples to use a more subtle background color that blends in with my dark theme background. I'll show you how to change it. Notice how the background of the Knockout Region (the data-bind attribute) stands out in the image below?
<a href="http://www.johnpapa.net/knockout-intellisense-in-visual-studio-2012/12-15-2012-9-30-55-pm/" rel="attachment wp-att-11021"><img src="http://www.johnpapa.net/wp-content/uploads/2012/12/12-15-2012-9-30-55-PM-600x39.png" alt="" title="12-15-2012 9-30-55 PM" width="600" height="39" class="aligncenter size-large wp-image-11021" /></a>

Under Tools | Options to to Environment and then Fonts and Colors. Then you can find the Knockout Region and you will likely want to change the Item Background color from its default. In my dark theme, the color was a bright grey by default. It made it really hard to read. So I changed it to a more subtle color. Hopefully this will change in the final release, but hey, its easy enough to change on your own (see below).

<a href="http://www.johnpapa.net/knockout-intellisense-in-visual-studio-2012/ko-region/" rel="attachment wp-att-11011"><img src="http://www.johnpapa.net/wp-content/uploads/2012/12/ko-region-600x348.png" alt="" title="ko region" width="600" height="348" class="aligncenter size-large wp-image-11011" /></a>

If you type multiple bindings in the same data-bind attribute, you'll separate them with a comma. When you type the comma you can again get intellisense for the available Knockout bindings. Very cool.

<h2>Custom Bindings</h2>
The cool part is that any custom bindings that you create are also accessible in the intellisense. In the SPA Template they give you 4 custom Knockout binding handlers. These are located in the <code class="keyword">todo.bindings.js</code> file which is included in the todo script bundle in the Index.cshtml view. Notice below how the blurOnEnter custom binding appears.
<a href="http://www.johnpapa.net/knockout-intellisense-in-visual-studio-2012/bluronenter/" rel="attachment wp-att-11071"><img src="http://www.johnpapa.net/wp-content/uploads/2012/12/bluronenter.png" alt="" title="bluronenter" width="569" height="290" class="aligncenter size-full wp-image-11071" /></a>

I'm a big fan testing new features so I know what works and what doesn't work. So I tested this out by creating a new JavaScript file called <code class="keyword">todo.mybindings.js</code>. I added a binding handler called fakeBinding to it. Then I added a reference to it in the <code class="keyword">/scripts/_references.js</code> file. Then I went back to the View and my fakeBinding showed up in the intellisense. This is a really nice feature. Of course, if you add a binding you'll want to include your new JavaScript file in the page too (in a script tag or in a script bundle).

<pre class="prettyprint linenums">
/// <reference path="jquery-1.8.2.js" />
/// <reference path="jquery-ui-1.9.2.js" />
/// <reference path="jquery.validate.js" />
/// <reference path="jquery.validate.unobtrusive.js" />
/// <reference path="knockout-2.2.0.debug.js" />
/// <reference path="modernizr-2.6.2.js" />
/// <reference path="app/todo.mybindings.js" />
/// <reference path="app/todo.bindings.js" />
/// <reference path="app/todo.datacontext.js" />
/// <reference path="app/todo.model.js" />
/// <reference path="app/todo.viewmodel.js" />
</pre>

<h2>ViewModel Members</h2>
Once you type the colon in the data-bind attribute you want to enter a member of your ViewModel. The intellisense is smart enough to see that you've bound the View to a ViewModel and it finds the accessible members in that ViewModel and lists them in the intellisense. In the SPA Template there are 4 accessible members of the ViewModel <code class="keyword">todoApp.todoListViewModel</code> that are exposed via the Revealing Module Pattern.
<pre class="prettyprint linenums">
    // returned from the module todoApp.todoListViewModel
    return {
        todoLists: todoLists,
        error: error,
        addTodoList: addTodoList,
        deleteTodoList: deleteTodoList
    };
</pre>
These now appear in the intellisense, as shown below.
<a href="http://www.johnpapa.net/knockout-intellisense-in-visual-studio-2012/vm-members/" rel="attachment wp-att-11081"><img src="http://www.johnpapa.net/wp-content/uploads/2012/12/vm-members-600x102.png" alt="" title="vm members" width="600" height="102" class="aligncenter size-large wp-image-11081" /></a>

When you add new members to the ViewModel they will appear in the intellisense list, too.

<h2>Module Pattern Is Helpful</h2>
If you use the Revealing Module Pattern, which is what the SPA Template and all of my SPA course material promotes, then you'll get the benefit of just the accessible members of the ViewModel to bind to. The reason this pattern is helpful here is that it limits what members of the module (the viewmodel) are exposed. This eliminates irrelevant members from the intellisense such as members that may be entirely internal to the module. <My advice is to use the pattern :) If you want to learn more about this pattern, you can check out my <a href="http://jpapa.me/komvvm" target="_blank">Knockout course specifically in the module "JavaScript Patterns: Spaghetti to Ravioli"</a> where I cover this topic.

<h2>From Here</h2>
I love this feature especially since I do a lot of Knockout. I see a lot of developers struggle with syntax since we're just typing in strings int he HTML with no guards against typos. It's very easy to mistype a binding or a view model member, but this feature should really help. I'd love to see this taken further, too, where we get dot intellisense for nested objects in the view model. This is entirely more complicated to achieve, but hey, it's my wish list! 
