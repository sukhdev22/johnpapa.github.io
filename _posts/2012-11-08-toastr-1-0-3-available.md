---
layout: post
title: Toastr 1.1.1 Available
date: 2012-11-08 03:19
author: John
comments: true
categories: [javascript, jquery, nuget, toastr, Uncategorized]
---
Just a few months ago <a href="http://twitter.com/hfjallemark">Hans Fjällemark</a> and I released toastr and since then we've had a lot of great feedback that we've worked into our free open source library. <a href="http://jpapa.me/c7toastr" target="_blank">Toastr is a simple JavaScript toast notification library</a> that is small, easy to use, and extendable. It allows you to create simple toasts with HTML5 and JavaScript like this:

<blockquote>Update: Version is now 1.1.1, since there was an API change (still backwards compatible) - added AMD support and version number.</blockquote>

<a href="/wp-content/uploads/media/Windows-Live-Writer/toastr_13960/image_2.png"><img style="background-image: none; padding-left: 0px; padding-right: 0px; display: inline; padding-top: 0px; border-width: 0px;" title="image" src="/wp-content/uploads/media/Windows-Live-Writer/toastr_13960/image_thumb.png" alt="image" width="377" height="79" border="0" /></a>

Simply include the files in your HTML page and write a simple line of code like this:
<pre class="prettyprint">toastr.success('Are you the six fingered man?', 'Inigo Montoya');</pre>
<p align="justify">Click the this button to try it yourself.</p>
<button id="tryToastrButton">Try toastr</button>
<link href="http://codeseven.github.com/toastr/toastr.css" rel="stylesheet" type="text/css" />
<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.6.3/jquery.min.js"></script>
<script src="http://codeseven.github.com/toastr/toastr.js"></script>
<script>
$('#tryToastrButton').click(function(){
    toastr.success('As you wish', 'Princess Bride Quotes');
});
</script>
<div></div>
<h2 align="justify">Get the Latest Bits for toastr 1.1.1</h2>
You can grab the latest bits from NuGet or github
<ul>
	<li>Install <a href="http://nuget.org/packages/toastr" target="_blank">toastr from NuGet</a></li>
	<li>Fork <a href="http://jpapa.me/c7toastr" target="_blank">toastr on github</a></li>
</ul>
<h2 align="justify">What's New in 1.1.1</h2>
<p align="justify">Today we finished the final changes for a new version of toastr (toastr 1.1.1). Here is a summary of the changes:</p>

<ul>
	<li>Now supports AMD modules or non AMD modules (still backwards compatible)</li>
	<li>Added version property to return toastr's  version</li>
</ul>
<pre class="prettyprint" style="padding-left: 30px;">console.log(toastr.version);</pre>
<ul>
	<li>Now requires jQuery 1.6.3 or later (formerly 1.7.2)</li>
	<li>Combined the 2 CSS files into 1 CSS file (contains all CSS and its media queries for responsive web design)</li>
	<li>Cleaned some outdated vendor prefixes in the CSS (thanks to <a href="http://jpapa.me/webess2012" target="_blank">Web Essentials 2012</a>)</li>
	<li>New clear method to clear all toasts</li>
</ul>
<pre class="prettyprint" style="padding-left: 30px;">toastr.clear();</pre>
<ul>
	<li>Added optionsOverride API to be able to override options for each toast,</li>
</ul>
<pre class="prettyprint linenums" style="padding-left: 30px;">var msg = 'Do you think Rodents of Unusual Size really exist?';
var title = 'Fireswamp Legends';
var overrides = {timeOut: 250};
toastr.warning(msg, title, overrides);</pre>
<ul>
	<li>Added onclick callback option which fires when a user clicks the toast.</li>
</ul>
<pre class="prettyprint linenums" style="padding-left: 30px;">toastr.options.onclick = function () {
    alert('You can perform some custom action after a toast goes away');
}

toastr.info('Build a SPA');</pre>
<h2 class="prettyprint linenums">Live Demo</h2>
Needs more information? Check out the readme on the github page for details on the simple API. You can also find a link to <a href="http://jpapa.me/c7toastr" target="_blank">the live toastr demo on github</a> or you can <a href="http://codeseven.github.com/toastr/" target="_blank">go directly to the toastr demo from here</a>.
