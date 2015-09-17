---
layout: post
title: AngularJS Code Snippets for Visual Studio
date: 2013-08-18 00:36
author: John
comments: true
categories: [angular, snippet, Uncategorized, visual studio 2012]
---
Controllers, services and directives are some of the core features in <a href="http://www.angularjs.org" target="_blank">AngularJS</a> where you'll end up writing a lot of your code. So why not reduce the friction and keep them consistent?

There is a lot of value in using consistent patterns in code. When I find myself using one, I create snippets to help me stick with the pattern. When the pattern evolves, I change the snippets to evolve with them. Recently I found myself using a similar pattern for create Angular controllers, factories/services and directives. So it just made sense to create Visual Studio snippets for each of them and share them. I use these and many other patterns in my upcoming course at <a href="http://www.pluralsight.com" target="_blank">Pluralsight</a> on using Angular and Breeze to build a powerful SPA.

<h2>AngularJS Snippets</h2>
There's a great set of <a href="http://msdn.microsoft.com/en-us/library/ms165394.aspx" target="_blank">simple instructions on this MSDN post</a> for creating snippets. I recommend reading this through so you can create your own, or modify mine to suit your needs.
<h2>Controllers</h2>
I created <a href="http://www.johnpapa.net/wp-content/uploads/files/downloads/ng-snippets.zip" target="_blank">snippets for creating controllers, services via factories, and directives</a> using a pattern that's emerged for me. You can <a href="http://www.johnpapa.net/wp-content/uploads/files/downloads/ng-snippets.zip" target="_blank">download them here</a>.

Once you grab these, go ahead and install them in Visual Studio. Type <code>CTRL K, CTRL B</code> to get to the Code Snippets Manager. Select JavaScript as the language, open My Code Snippets, then click the import button. Locate each snippet and import them.
<pre class="prettyprint linenums">
(function () {
    'use strict';
    var controllerId = 'customController';
    angular.module('app').controller(controllerId,
        ['$scope', customController]);
    function customController($scope) {
        var vm = this;
        vm.activate = activate;
        function activate() {
        }
        //#region Internal Methods        
        //#endregion
    }
})();
</pre>
Once you have the snippets, simply type the shortcut for the snippet you want followed by the <code>TAB</code> key and the snippet will appear. For example, when you type <code>ngctrl</code> followed by <code>TAB</code> you will see the code shown above. I use this when I open a file and create a new controller from scratch. The snippets prompt me to fill in all of the customizable parts such as module name, controller name, and first of the dependencies.
<h2>Diversion to Controller As</h2>
It also lays out the structure for how I like my controllers to look. For example, I often use the <code>controller as</code> syntax (<a href="http://www.youtube.com/watch?v=tTihyXaz4Bo" target="_blank">learn more here in John Lindquist's video</a>) which melds nicely with writing the properties that I want to bind inside my View using the <code>this</code> syntax. Say what? OK, so basically I create a viewmodel variable called <code>vm</code> and I set all of my bindable members on it. Then that becomes the part that gets bound to the View when using the <code>controller as</code> syntax. So I create <code>vm</code> and set it to <code>this</code>. Then all of the properties on that object become bindable.
<pre class="prettyprint linenums">
function sessions(config) {
    var vm = this;
    var keyCodes = config.keyCodes;
    var applyFilter = function (){};
    vm.refresh = refresh;
    vm.search = search;
    vm.sessions = [];
    vm.title = 'Sessions';
</pre>
<h2>Services</h2>
The <code>ngservice</code> snippet will create the code for a service factory. Again, the snippet will prompt you to fill in the customizable aspects. Then you can fill in the accessible members of the service by setting them on the <code>service</code> object. Here I start with one called getData as a starting place. This is akin to the Revealing Module Pattern which helps expose the members we want to be accessible, yet keep other internal. This is ideal for any service that may get/save data, log, store to local storage, or perform any custom service you need.
<pre class="prettyprint linenums">
(function () {
    'use strict';
    var serviceId = 'customService';
    angular.module('app').factory(serviceId, 
        ['config', customService]);
    function customService(config) {
        var service = {
            getData: getData
        };
        return service;
        function getData() {
        }
        //#region Internal Methods        
        //#endregion
    }
})();
</pre>
<h2>Directives</h2>
The <code>ngdir</code> snippet creates the beginnings of a directive. The snippet let you fill in the module name, directive name, first of the dependencies, and provides a structure for setting the aspects of a directive (such as the <code>link</code> function). It also provide the comments I often use with a directive to help me recall how to call the directive, and what the directive creates (if it has a template). Again, this is a starting point for a directive, and quite often I will add more to it (ex: scope, template, compile). But this is a nice common place to get it all started.
<pre class="prettyprint linenums">
app.directive('customDirective', 
        ['$window', function ($window) {
    // Usage:
    // 
    // Creates:
    // 
    var directive = {
        link: link,
        restrict: 'A'
    };
    return directive;
    function link(scope, element, attrs) {
    }
}]);
</pre>
<h2>Consistency</h2>
It is not important to use the patterns that I use. What is important is for you to use a pattern and be consistent within your own app. The patterns are helpful but another thing these snippets help with is minification protection for the injected dependencies. This can sometimes be forgotten when coding fast, so these snippets help me set that in place without having to think about it (or before I forget about it).

I'll continue to evolve these over time and certainly I hope these are as useful to you as they are to me!

