---
layout: post
title: New Breeze Angular Service 
date: 2014-03-25 04:36
author: John
comments: true
categories: [angular, breeze, hottowel, javascript, pluralsight, Uncategorized]
---
<p>The world of JavaScript changes at a fast pace and in the time since my <a href="http://jpapa.me/spangz">Angular and Breeze Part 1</a> and <a href="http://jpapa.me/spangz2">Angular and Breeze Part 2</a> Pluralsight courses have been released, both libraries have had some revisions. One such revision is worth making some changes in your code. The good news is that the folks at <a href="http://angularjs.org">Angular</a> and <a href="http://breezejs.com">Breeze</a> made it easier on us all. This post explains the changes and how you can refactor your code quickly to work with the latest Angular and Breeze libraries.</p>

<h3>Short Version</h3>

<p>With HotTowel.Angular.Breeze 2.1.0 (and prior), we used to need these 3 files:</p>

<ul>
<li><code>scripts/breeze.angular.q.js</code></li>
<li><code>scripts/breeze.directives.validation.js</code></li>
<li><code>app/config.breeze.js</code></li>
</ul>

<p>If you had that code, you can safely replace it with these files:</p>

<ul>
<li><code>scripts/breeze.angular.js</code></li>
<li><code>scripts/breeze.directives.js</code></li>
<li><code>scripts/breeze.to$q.shim.js</code> (optional shim ... read more on this down below)</li>
</ul>

<p>Then remove all references to <code>config.breeze</code>.</p>

<p>If you want to rid yourself of the <code>breeze.to$q.shim.js</code> entirely, simply replace all of the places in your code where you see <code>to$q</code> with <code>then</code>.</p>

<p>Or, if you are starting from scratch, simply run <code>install-package HotTowel.Angular.Breeze</code> which will get you version 2.2.0 and the correct files.</p>

<p>The <code>entityManagerFactory.js</code> file has changed from HotTowel.Angular.Breeze 2.1.0 to 2.2.0. You should be sure to use the newer file.</p>

<blockquote>
  <p>I'll be updating my Angular and Breeze Pluralsight courses to show this change soon.</p>
</blockquote>

<h3>Q and $q</h3>

<p>Why the changes? Well let's break it down. The <code>breeze.angular.q.js</code> file no longer exists. It used to handle converting Q to $q between Breeze and Angular. This is thankfully no longer needed, so let's say goodbye to it.</p>

<h3>breeze directives</h3>

<p>The <code>breeze.directives.validation.js</code> file used to contain the breeze validation directive. Since then, there are other directives the Breeze folks have added, so they renamed the file to account for that and now they live in <code>breeze.directives.js</code>.</p>

<h3>to$q shim</h3>

<p>When the Q to $q issue went away, unfortunately all of the code in my course still referenced it. So there is a shim file named <code>breeze.to$q.shim.js</code> just for this purpose. It allows you to write Breeze queries that use the <code>to$q</code> function in place of a <code>then</code>. This shim only exists to help with my course. So if you are working through my course, and you replace every place you see <code>to$q</code> with a <code>then</code> you will no longer need this shim file either.</p>

<h3>Angular Breeze Service</h3>

<p>The file <code>config.breeze.js</code> used to help us configure Breeze for Angular. One night I was chatting with my friend Ward Bell at IdeaBlade (makers of Breeze) and I asked why they didn't create a Breeze configuration service. The Breeze team soon thereafter created the <code>breeze.angular.js</code> file, which contains the <code>breeze</code> Angular service. This service configures Breeze to be "Angular Ready". And thus the need for<code>config.breeze.js</code>was soon gone and replaced with<code>breeze.angular.js</code>. This is great because now we just add that file and its all set to go. Before, we had to write the code to make Breeze ready for Angular.</p>

<h3>The Whole Sha-Bang</h3>

<p>If you start from scratch and use HotTowel.Angular.Breeze version 2.2.0, you are presented with instructions to add these files to your project. Then you simply add the modules <code>breeze.angular</code> and <code>breeze.directives</code> as dependencies to your application's module and you are off to the races!</p>

<pre><code>&lt;link href="content/breeze.directives.css" rel="stylesheet" /&gt;

&lt;script src="scripts/breeze.debug.js"&gt;&lt;/script&gt;
&lt;script src="scripts/breeze.angular.js"&gt;&lt;/script&gt;
&lt;script src="scripts/breeze.directives.js"&gt;&lt;/script&gt;
&lt;script src="scripts/breeze.saveErrorExtensions.js"&gt;&lt;/script&gt;

&lt;script src="scripts/breeze.to$q.shim.js"&gt;&lt;/script&gt; &lt;!-- Needed only if you are using to$q --&gt;

&lt;script src="app/services/entityManagerFactory.js"&gt;&lt;/script&gt;
</code></pre>

<p>Update your app.js to include the breeze modules</p>

<pre><code>(function () {
    'use strict';

    var app = angular.module('app', [
        // Angular modules 
        'ngAnimate',        // animations
        'ngRoute',          // routing
        'ngSanitize',       // sanitizes html bindings (ex: sidebar.js)

        // Custom modules 
        'common',           // common functions, logger, spinner
        'common.bootstrap', // bootstrap dialog wrapper functions

        // 3rd Party Modules
        'breeze.angular',    // configures breeze for an angular app
        'breeze.directives', // contains the breeze validation directive (zValidate)
        'ui.bootstrap'       // ui-bootstrap (ex: carousel, pagination, dialog)
    ]);

    // Handle routing errors and success events.
    // Trigger breeze configuration
    app.run(['$route', function ($route) {
            // Include $route to kick start the router.
        }]);        
})();
</code></pre>

