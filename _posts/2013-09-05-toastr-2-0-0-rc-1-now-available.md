---
layout: post
title: Toastr 2.0.0 rc 1 Now Available
date: 2013-09-05 05:30
author: John
comments: true
categories: [github, nuget, toastr, Uncategorized]
---
Toastr 2.0.0 is now at Release Candidate 1. You can grab the <a href="https://github.com/CodeSeven/toastr" target="_blank">Toastr 2 RC on GitHub</a> or <a href="http://www.nuget.org/packages/toastr" target="_blank">get Toastr 2 RC on NuGet</a> using <code> install-package toastr - pre</code>. This release has several minor bug fixes, CSS tweaks, some JavaScript refactoring, and some new features. Of course there are new unit tests for all of these too. There is 1 breaking change that I felt was in the best interest, which is why this is a new major version. 

Please read below and try Toastr out. Once enough folks have had a chance to give it whirl and report bacl, I'll release another RC or final soon!

<blockquote>Toastr is now at over 50,000 downloads on NuGet! Thank you for using Toastr and to the many folks who have contributed through issues and pull requests on the Toastr GitHub site.  </blockquote>

Note: Once version 2 is fully released I will also update Bower, Grunt, and CDNJS.

<h2>Animation Changes (Breaking)</h2>
The following animations options have been deprecated and should be replaced:
<ul>
	<li>Replace <code>options.fadeIn</code> with <code>options.showDuration</code></li>
	<li>Replace <code>options.onFadeIn</code> with <code>options.onShown</code></li>
	<li>Replace <code>options.fadeOut</code> with <code>options.hideDuration</code></li>
	<li>Replace <code>options.onFadeOut</code> with <code>options.onHidden</code></li>
</ul>
<h2>Animation Options (New)</h2>
Toastr will supply default animations, so you do not have to provide any of these settings. However you have the option to override the animations if you like.
<h3>Easings</h3>
Optionally override the animation easing to show or hide the toasts. Default is swing. swing and linear are built into jQuery.
<pre class="prettyprint">toastr.options.showEasing = 'swing';
toastr.options.hideEasing = 'linear';</pre>
Using the jQuery Easing plugin (<a href="http://www.gsgd.co.uk/sandbox/jquery/easing/">http://www.gsgd.co.uk/sandbox/jquery/easing/</a>)
<pre class="prettyprint">toastr.options.showEasing = 'easeOutBounce';
toastr.options.hideEasing = 'easeInBack';</pre>
<h3>Animation Method</h3>
Use the jQuery show/hide method of your choice. These default to fadeIn/fadeOut. The methods fadeIn/fadeOut, slideDown/slideUp, and show/hide are built into jQuery.
<pre class="prettyprint">toastr.options.showMethod = 'slideDown'; 
toastr.options.hideMethod = 'slideUp';</pre>
<h2>Close Button (New)</h2>
Optionally enable a close button
<pre class="prettyprint">toastr.options.closeButton = true;</pre>
Optionally override the close button's HTML.
<pre class="prettyprint">toastr.options.closeHtml 
    = '<button><i class="icon-off"></i></button>';</pre>
You can also override the CSS/LESS for <code>#toast-container .toast-close-button</code>
<h2>Display Sequence (New)</h2>
Show newest toast at bottom (top is default)
<pre class="prettyprint">toastr.options.newestOnTop = false;</pre>

Thanks to the folks who contributed issues or pull requests to this release including: Ryan Hoffman, Jon Gallant, Jon Fazzaro, Craig Teegarden, Umberto, and Raffi.
