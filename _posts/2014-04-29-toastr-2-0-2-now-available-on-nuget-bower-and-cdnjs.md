---
layout: post
title: Toastr 2.0.2 Now Available on NuGet, Bower and CDNJS
date: 2014-04-29 23:36
author: John
comments: true
categories: [toastr, Uncategorized]
---
<p>Toastr 2.0.2 is now available on Bower, NuGet and CDNJS! We're thrilled that toastr has been so helpful to many of you as it now has almost 150,000 downloads on NuGet and 1600+ stars on github!</p>

<p>This release has several minor bug fixes and some new features. For details you can check out the <a href="https://github.com/CodeSeven/toastr/blob/master/CHANGELOG.md">changelog</a>. Of course there are new unit tests for all of these too.</p>

<h2>Get Toastr</h2>

<ul>
<li><a href="https://github.com/CodeSeven/toastr">Toastr on GitHub</a> </li>
<li><a href="https://www.nuget.org/packages/toastr/">Toastr on NuGet</a> using <code>install-package toastr</code> </li>
<li><a href="http://bower.io/search/?q=toastr">Toastr on Bower</a> </li>
<li><a href="http://www.cdnjs.com/libraries/toastr.js">Toastr on CDNJS</a></li>
</ul>

<h2>Learning Toastr</h2>

<p>The <a href="http://codeseven.github.io/toastr/demo.html">Toastr demo page</a> is also updated to help demonstrate the features.</p>

<h2>New Features</h2>

<ul>
<li>Added simple ARIA reader support</li>
<li>Added SASS support</li>
</ul>

<h2>Bug Fixes</h2>

<ul>
<li>Added sourcemap for the min file </li>
<li>IE 8 does not support stopPropagation on the event </li>
<li>Media query width fixes </li>
<li>Fix of onHidden firing twice when clicking on it then moving mouse out of toast </li>
<li>Clear all toasts followed by a new toast now displays correctly</li>
</ul>

<h2>Contributions</h2>

<p>Thanks to the community for their contributions to Toastr as always. This version had pull requests accepted from <a href="https://github.com/CodeSeven/toastr/commit/b4c8b3460efb8aa51c730dd38c35ef6b025db2cc">Darren Haken</a>, <a href="https://github.com/CodeSeven/toastr/commit/45c63628476f6b085a6579dc681f4fe61ba5820c">Greta Krafsig</a>, and <a href="https://github.com/CodeSeven/toastr/commit/698957325a8e7bf63990f71ee409b911d69bc8ec">ddotm</a>.</p>

<p>I am always happy to consider pull requests for toastr provided that they are for a compelling new feature or a bug fix, and they include a unit test. I reserve the right to choose which come into toastr so the product stays true to its core, which is to be a lightweight alerting library.</p>

