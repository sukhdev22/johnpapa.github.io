---
layout: post
title: Get Angular, Durandal, and JavaScript Templates with SideWaffle
date: 2013-08-27 02:12
author: John
comments: true
categories: [angular, durandal, javascript, Uncategorized, visual studio 2012]
---
<img src="http://sidewaffle.com/img/logo.png" width="96" height="96" class="alignright" />Hungry for some file templates to get you started in the morning? Well now you can fill up on a set of web template packs for Visual Studio 2012 and 2013. <a href="http://www.sidewaffle.com" target="_blank">SideWaffle</a> is an open source project that creates a Visual Studio extension containing a set of file templates you can use for web projects. 

SideWaffle currently has several templates including 10 I contributed for <a href="http://www.angularjs.org" target="_blank">Angular</a>, <a href="http://www.durandaljs.com" target="_blank">Durandal</a>, and creating a JavaScript IIFE. One of the best parts is that SideWaffle will be frequently updated with new and useful templates (they do check for high quality templates). I expect that in the near term we'll see a lot of additions.
<ul>
<li>Angular Controller (using Controller As syntax)</li>
<li>Angular Controller (using $scope)</li>
<li>Angular Directive (creates a skeleton for a directive)</li>
<li>Angular Factory (great for data, logging, and other services)</li>
<li>Angular Module (sets up a module)</li>
<li>Durandal ViewModel</li>
<li>Durandal Service</li>
<li>Durandal main.js (common creation syntax for kicking off Durandal)</li>
<li>JavaScript IIFE (Basic IIFE using vanilla.js)
</ul>
I use the Angular templates in my upcoming course at <a href="http://www.pluralsight.com" target="_blank">Pluralsight</a> on using Angular and Breeze to build a powerful SPA.
<h2>What's in it for You?</h2>
Imagine you are in a web project writing Angular code. You want to create a new Angular controller. What do you do today? You might create a new JavaScript file and use a <a href="http://www.johnpapa.net/angularjs-code-snippets-for-visual-studio/" target="_blank">code snippet like my <code>ngctrl</code> snippet</a>, or you could write it from scratch. But now with SideWaffle you can click <code>CTRL+SHIFT+A</code> to add a new file and choose the Angular Controller file template from SideWaffle. 
<img src="http://www.johnpapa.net/wp-content/uploads/2013/08/SideWaffle-600x452.png" alt="SideWaffle" width="600" height="452" class="aligncenter size-large wp-image-20321" />

So when you open the Add New Item dialog, choose the SideWaffle sub-folder (just to narrow the scope) and/or search for the template name in the search box. Then select the template and enter the name for the file. Some of the templates will use the file and/or project name where appropriate in generating the file. Below is an example of what the Angular Controller template generates when you name the file <code>sessions.js</code>. The whole idea is to get you started.
<pre class="prettyprint linenums">
(function () {
    'use strict';

    // Controller name is handy for logging
    var controllerId = 'sessions';

    // Define the controller on the module.
    // Inject the dependencies. 
    // Point to the controller definition function.
    angular.module('app').controller(controllerId,
        ['$scope', sessions]);

    function sessions($scope) {
        // Using 'Controller As' syntax, so we 
        // assign this to the vm variable (for viewmodel).
        var vm = this;

        // Bindable properties & functions are placed on vm
        vm.activate = activate;
        vm.title = 'sessions';

        function activate() {
        }

        //#region Internal Methods        

        //#endregion
    }
})();
</pre> 

Or imagine you are creating a module for your Angular app and you forgot the exact syntax to use. You can use the Angular Module template from SideWaffle and name the file app.js and it would generate the following code.
<pre class="prettyprint linenums">
(function () {
    'use strict';

    // Module name is handy for logging
    var id = 'app';

    // Create the module and define its dependencies.
    var app = angular.module('app', [
        // Angular modules 
        'ngAnimate',        // animations
        'ngRoute'           // routing

        // Custom modules 

        // 3rd Party Modules
        
    ]);

    // Execute bootstrapping code and any dependencies.
    app.run(['$q', '$rootScope',
        function ($q, $rootScope) {

        }]);
})();
</pre>
Notice the template puts a few dependencies in for some common modules such as <code>ngRoute</code> and <code>ngAnimate</code>. it also reminds you to add any other custom or 3rd party modules in the dependency list. Then it creates the kickoff code in <code>app.run</code>, injecting <code>$q</code> and <code>$rootscope</code>, two common dependencies. As a template, you can then modify whatever you need, of course.

The Durandal and JavaScript IIFE templates work in a similar fashion. Grab the SideWaffle VSIX, install it and give it a shot!
<h2>Contribute</h2>
Because it is open source, you can fork the repository, add your own templates, and make a pull request. The repository is managed by <a href="https://twitter.com/mkristensen" target="_blank">Mads Kristensen</a> and <a href="https://twitter.com/sayedihashimi" target="_blank">Sayed Hashimi</a>.

So if you are interested in creating a new template, dig in. Quoting Mads ...
<blockquote>We’ve made sure to modify the project’s build system, so it automatically creates the VSIX based on the items in the project. Writing item templates have never been this easy. See the video below, it explains everything. The project is a VSIX containing item templates for all kinds of web related scenarios. For instance robots.txt, requireJS scaffolds etc.
</blockquote>

Here is a quick video from Mads that tells you pretty much all you need to know on what they are and how to create one.
<iframe width="420" height="315" src="//www.youtube.com/embed/h4VaORKgrOw" frameborder="0" allowfullscreen></iframe>
