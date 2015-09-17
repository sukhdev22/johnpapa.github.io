---
layout: post
title: Toastr 1.3.0 Now Available
date: 2013-05-09 23:23
author: John
comments: true
categories: [github, nuget, open source, toastr, Uncategorized]
---
One year ago this month <a href="http://twitter.com/hfjallemark">Hans Fjällemark</a> and I released Toastr and are happy to see that developers seem to appreciate its simplicity. It's now be downloaded on NuGet over 27,000 times. In fact, the recent version was downloaded over 10,000 times the past 2 months! Today we have released version 1.3.0 to github and NuGet.

<a href="http://jpapa.me/c7toastr" target="_blank">Toastr is a simple JavaScript toast notification library</a> that is small, easy to use, and extendable. It allows you to create simple toasts with HTML5 and JavaScript like this:

<a href="/wp-content/uploads/media/Windows-Live-Writer/toastr_13960/image_2.png"><img style="background-image: none; padding-left: 0px; padding-right: 0px; display: inline; padding-top: 0px; border-width: 0px;" title="image" src="/wp-content/uploads/media/Windows-Live-Writer/toastr_13960/image_thumb.png" alt="image" width="377" height="79" border="0" /></a>

Simply include the files in your HTML page and write a simple line of code like this:
<pre class="prettyprint linenums">
var msg = 'Are you the six fingered man?';
var title = 'Inigo Montoya';
toastr.success(msg, title);</pre>
<p align="justify">Click the this button to try it yourself.</p>
<button id="tryToastrButton">Try Toastr</button>
<link href="http://codeseven.github.io/toastr/toastr.css" rel="stylesheet" type="text/css" />
<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.6.3/jquery.min.js"></script>
<script src="http://codeseven.github.io/toastr/toastr.js"></script>
<script>
$('#tryToastrButton').click(function(){
    toastr.success('As you wish', 'Princess Bride Quotes');
});
</script>
<h3>Get Toastr 1.3.0</h3>
You can grab the latest bits from NuGet or github
<ul>
	<li>Install&nbsp;<a href="http://nuget.org/packages/toastr" target="_blank">toastr from NuGet</a></li>
	<li>Fork <a href="http://jpapa.me/c7toastr" target="_blank">toastr on github</a></li>
</ul>

<h3>What's New in 1.3.0</h3>
<ul>
	<li>Added onFadeIn and onFadeOut callbacks.</li>
</ul>
<pre class="prettyprint linenums">
toastr.options.onFadeIn = 
    function() { 
        console.log('hello'); 
    };
</pre>
<ul>
<li>Added option <code>newestOnTop</code> to show toasts in oldest or newest first order.</li>
</ul>
<pre class="prettyprint">
toastr.options.newestOnTop = false;
</pre>
<ul>
<li>Fixed margins on full width toasts</li>
<li>Added LESS file.</li>
<li>Added min file for JS and CSS</li>
<li>Added missing vendor prefixes in CSS.</li>
<li>Various minor bug fixes.</li>
<li>Added unit tests for new features.</li>
</ul>

<h3 class="prettyprint linenums">Live Demo</h3>
Needs more information? Check out the readme on the github page for details on the simple API. You can also find a link to <a href="http://jpapa.me/c7toastr" target="_blank">the live toastr demo on github</a> or you can <a href="http://codeseven.github.com/toastr/" target="_blank">go directly to the toastr demo from here</a>.



<blockquote>Some of these features came right from pull requests from Toastr users. If you have an idea for Toastr, feel free to contribute and make a pull request. just be sure to also include unit tests to cover any code changes.
</blockquote>


