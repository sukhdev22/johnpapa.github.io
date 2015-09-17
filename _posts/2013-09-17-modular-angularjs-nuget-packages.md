---
layout: post
title: Modular AngularJS NuGet Packages
date: 2013-09-17 23:48
author: John
comments: true
categories: [angular, nuget, Uncategorized]
---
<p><img src="http://www.johnpapa.net/wp-content/uploads/2013/09/angular-icon.png" alt="angular-icon" width="96" height="96" class="alignleft size-full wp-image-21531" />Now serving smaller bite sized AngularJS NuGet packages! AngularJS 1.2 shifted to a more modular approach where the core AngularJS features are in angular.js while other functionality such as routing, animation, and resource are located in their own separate files. Each file hosts a module that you can optionally include in your project.</p>

<blockquote>
  <p><strong>UPDATE</strong>: This page will serve as a sticky page to jump directly to all of the packages. See the list below.  Since there are now a bunch of files for the various modules and there are dozens of internationalization files for angular, the AngularJS super NuGet package can feel overwhelming if you don't want all of it. if you do want all or most of it, then its still a great package. But if you want to pick and choose, well, that's where these new packages may interest you. <a href="https://twitter.com/shanselman" target="_blank">Scott Hanselman</a> and I maintain a series of Angular NuGet packages (see below) that have the philosophy of '1 Package Per Module'. There is the <code>AngularJS.Core</code> package which contains angular.js, angular.min.js, angular.min.js.map, and angular.mocks.js. These are the core files for an angular project (mocks for testing). All of the other packages listed below depend on the AngularJS.Core package and add their appropriate feature/module. 
  *   <a href="https://www.nuget.org/packages/AngularJS.Core" target="_blank">AngularJS.Core</a>
  *   <a href="https://www.nuget.org/packages/AngularJS.Animate" target="_blank">AngularJS.Animate</a>
  *   <a href="https://www.nuget.org/packages/AngularJS.Cookies" target="_blank">AngularJS.Cookies</a>
  *   <a href="https://www.nuget.org/packages/AngularJS.Loader" target="_blank">AngularJS.Loader</a>
  *   <a href="https://www.nuget.org/packages/AngularJS.Locale" target="_blank">AngularJS.Locale</a>
  *   <a href="https://www.nuget.org/packages/AngularJS.Resource" target="_blank">AngularJS.Resource</a>
  *   <a href="https://www.nuget.org/packages/AngularJS.Route" target="_blank">AngularJS.Route</a>
  *   <a href="https://www.nuget.org/packages/AngularJS.Sanitize" target="_blank">AngularJS.Sanitize</a>
  *   <a href="https://www.nuget.org/packages/AngularJS.Touch" target="_blank">AngularJS.Touch</a> These packages are currently available and you can install them by running:</p>
</blockquote>

<pre class="prettyprint">Install-Package AngularJS.Core</pre>

<p>This will install the core AngularJS files.</p>

