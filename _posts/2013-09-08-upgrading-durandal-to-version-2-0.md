---
layout: post
title: Upgrading to Durandal 2.0
date: 2013-09-08 14:14
author: John
comments: true
categories: [durandal, javascript, SPA, Uncategorized]
---
Recently I upgraded a few projects from Durandal v1.x to <a href="http://durandaljs.com/" target="_blank">Durandal 2.0</a>. I did these before there were any notes on the Durandal site for upgrading so I took a bunch of notes. I was lucky enough that the first conversion was aided with the direct help of <a href="https://twitter.com/EisenbergEffect" target="_blank">Rob Eisenberg</a>, creator of Durandal. Rob has since created a great page in the docs to help you <a href="http://durandaljs.com/documentation/Conversion-Guide/" target="_blank">convert from 1.x to 2 which you can find here</a>. But I also included all of my raw notes in this post. Rob's is the definitive guide, but hopefully my brain dump may help some of you too :)

Please excuse the grammar below as it was a raw brain dump over the course of an hour.

<h2>Structure</h2>
This section covers all of the structural changes when I moved to Durandal 2.
<h3>Library Location</h3>
<ul>
	<li>All files are now located in the Scripts/durandal folder</li>
	<li>Plugins now include: dialog, history, http, observable, router, serializer, widget</li>
	<li>Transitions are still in their own folder</li>
</ul>
<h3>Observable</h3>
The observable plugin takes any Plain Old JavaScript Object (POJO) and adds observability to it. Works on property by property basis. You can also use the API to subscribe, create computed properties or retrieve the underlying observable.
<h3>RequireJS Setup</h3>
Because Durandal is now moved out of the app, you need a requirejs.config setup:
<pre class="prettyprint linenums">requirejs.config({
    paths: { 
        'text': '../Scripts/text',
        'durandal': '../Scripts/durandal',
        'plugins': '../Scripts/durandal/plugins',
        'transitions': '../Scripts/durandal/transitions'
    }
});
</pre>
<h3>RequireJS Changes</h3>
Durandal 2.x assumes no global libraries. It will ship expecting Knockout and jQuery to be defined with requirejs. The .NET templates by default will set them up as standard script libs and then register them with require as follows:
<pre class="prettyprint">
define('jquery', function () { return jQuery; });
define('knockout', ko);
</pre>
No need to setup requirejs.config paths for this. Developers who wish to pipe everything through require.js now have that capability, but the default .NET starter kit will use the same approach as 1.x.
<h3>main.js</h3>
Remove from main.js <code>app.AdaptToDevice()</code>
<h3>Global replaces</h3>
<ul>
	<li>Change paths for durandal plugins from <code>durandal/plugins/router</code> to <code>plugins/router</code></li>
	<li>rename <code>viewAttached</code> to <code>attached</code></li>
</ul>
<h3>router</h3>
Durandal 2 now has its own custom router, removing the Sammy dependency.
<ul>
	<li><code>router.visibleRoutes</code> is now <code>router.navigationModel</code></li>
	<li><code>router.allRoutes()</code> is now <code>router.routes</code> and is just an array</li>
	<li><code>routes</code> no longer have a <code>caption</code> nor <code>setting</code> property</li>
	<li><code>router.navigateTo</code> is now <code>router.navigate</code></li>
        <li>remove sammy.js and update index.html</li>
</ul>
<h3>route array changes</h3>
<ul>
	<li><code>url</code> is now renamed to <code>route</code></li>
	<li>because I use <code>router.makeRelative()</code> I can omit the full path to the <code>moduleId</code>. So <code>moduleId: 'viewmodels/sessions',</code> becomes <code>moduleId: 'sessions'</code></li>
	<li><code>visible</code> is now called <code>nav</code></li>
	<li><code>name</code> is now <code>title</code></li>
	<li>default route is now '' (empty string)</li>
</ul>
<h3>router parameter changes</h3>
Durandal v2.0 now passes in a parameter for each value. Query-string, if present, would be the last parameter.

In 1.2, <code>activate</code> used to pass an object.
<pre class="prettyprint linenums">//activate = function (routeData) {
activate = function (id, querystring) {
    //var id = parseInt(routeData.id);
    initLookups();
    return datacontext.getSessionById(id, session);
}
</pre>
<h3>router.replaceLocation</h3>
<code>replaceLocation</code> now accepts a url and a second parameter, which is an object literal. We can pass a value for <code>replace</code> and set to true, if we want to replace the route history.
<pre class="prettyprint linenums">function goToEditView(result) {
    var url = '#/sessiondetail/' + session().id();
    router.navigate(url, {replace: true});
}
</pre>
<h2>Lifecycle</h2>
<h3>activate</h3>
Activate no longer needs to return a promise and is automatically called for every composed object, without the need for an activator or additional configuration. Can remove <code>return</code> from all <code>activate</code> calls. If you return a promise, it will wait til the promise is done. But if we don't return a promise, no need to return.
<h3>binding</h3>
<ul>
	<li>formerly known as <code>beforeBind</code></li>
	<li>after <code>activate</code>, and immediately before <code>ko.applyBindings</code> is called</li>
	<li>can also return applyBindings: false</li>
	<li>can return object with instructions</li>
</li>
</ul>
<pre class="prettyprint linenums">// only this vm's view wont be cached
return { cacheViews: true } 
</pre>
<h3>bindingComplete</h3>
Fires after the binding has happened.
<h3>attached</h3>
Formerly known as <code>viewAttached</code>.
<pre class="prettyprint linenums">function attached(view, parent){ ... }
</pre>
<h3>compositionComplete</h3>
<ul>
	<li>New event (almost was called documentAttached)</li>
	<li>Fires whenever the composition that this module is participating in is entirely done (all parents and children compositions)</li>
	<li>Fires from child bubbling up to parent</li>
	<li>Useful for "measurement of an element", such as after the layout has been rendered</li>
	<li>You can also use <code>composition.addBindingHandler</code> to register (or convert) a standard binding handler into one that runs after composition completion.</li>
</ul>
<h3>detached</h3>
New event that fires when the view has been detached from the DOM
<h3>canDeactivate</h3>
Fires before you deactivate a viewmodel, providing an opportunity to cancel. Only present with an activator.
<h3>canActivate</h3>
Fires before you activate a viewmodel, providing an opportunity to cancel.O nly present with an activator
<h3>deactivate</h3>
Fires when a viewmodel is being deactivated. Only present with an activator.
<h3>Activator</h3>
No need to return a promise from activate anymore. You get activate without an activator now, too. Three ways to get an activator:
<ul>
	<li>router</li>
	<li>dialogs</li>
	<li>create and use one your self via <code>activator.create()</code> (formerly <code>viewModel.activator()</code>)</li>
</ul>
<h2>Configuring Plugins</h2>
You can now configure plugins prior to <code>app.start()</code>. Some plugins want to do things at start-up, so this helps them. For example <code>app.showDialog</code> and <code>app.showMessage</code> are extended on the app module by including it in the configuration.
<pre class="prettyprint linenums">app.configurePlugins({
    router: true,
    dialog: true,
    widget: {
        kinds: ['expander']
    }
});
</pre>
<h2>Router Binding</h2>
Faster, simpler, smaller. New router supports hash change and push-state. Better support for parameterized routes, splats, querystring parameters, and optional parameters. Deep linking supports is improved with custom callbacks and child routers. Lots of events are fired and tons of extensibility. Better support for "not found" routes and custom routing conventions. No SammyJS. Built from scratch with no dependencies outside of Durandal. Split into to modules: history and router. Don't like our router semantics? Write your own on top of history without having to muck with browser stuff.
<code>ko.bindingHandlers.router</code> gets installed with this plugin.
<pre class="prettyprint linenums">
<!-- ko router: 
    {transition: 'entrance', cacheViews: true } -->
<!-- /ko -->
</pre>
This is the same thing, just long-hand
<pre class="prettyprint linenums">
<!--ko compose: {
         model: router.activeItem,
         compositionComplete: router.compositionComplete,
         attached: router.attached,
         cacheViews:true,
         transition: 'entrance'} -->
<!--/ko-->
</pre>
This is a wrapper around the <code>compose</code> binding and makes binding router content simple.
<h3>Child Routing</h3>
We can nest routes. See examples for details
<h3>Activate Callback</h3>
Parameters come in as a list of parameters. Query-string comes in as the last argument (if present), and is keyed (object literal)
<h3>Mapping</h3>
Pass an array of objects with route, moduleId, title, nav, hash (and any custom data you want). <code>visible</code> is now called <code>nav</code>
<h4>Routing Sample</h4>
<pre class="prettyprint linenums">define (['plugins/router'], function (router) {
    return {
        router: router, 
        activate: function() {
            router.makeRelative({moduleId: 'viewmodels'});

            router.map([
                { route: '', 
                    moduleId: 'helloindex', 
                    title 'Hello World', 
                    nav: 1},
                { route: '/bye', 
                    moduleId: 'goodbye', 
                    title 'See ya', 
                    nav: 2}
            ]);

            //builds an observable model from the 
            //mapping to bind your UI to
            router.buildNavigationModel(); 

            //sets up conventional mapping for 
            //unrecognized routes
            router.mapUnknownRoutes(); 

            //activates the router
            return router.activate(); 
            // no longer needs a start module
        }
    }
});
</pre>
<h3>Use convention</h3>
<code> useConvention</code> has been replaced with <code>router.makeRelative({moduleId: 'viewmodels'});</code>
<h3>unknown routes</h3>
<pre class="prettyprint linenums">router.mapUnknownRoutes('moduleIdGoesHere'); 
//maps unknown routes to a single module
</pre>
Or pass it a function
<pre class="prettyprint linenums">router.mapUnknownRoutes(function(instruction){
    // custom routing logic to implement 
    // your own conventions. simply configure 
    // the instruction object and the router 
    // will handle it
});
</pre>
You can also define your own conventions. There will be a default (plugin config setting), but can override this.
<pre class="prettyprint linenums">router.on('router:route:before-config')
    .then(function (config) {
        config.moduleId = 'viewmodels/' + config.moduleId;
});
</pre>
<h2>Compose</h2>
New features for the compose binding:
<h3>Inline Views</h3>
Can now compose an inline view:
<pre class="prettyprint linenums"><!-- ko compose: { 
    model: 'viewComposition/inlineModule', 
    mode: 'inline' } -->
    <div>Some inlined view bound against the model.</div>
<!-- /ko -->
</pre>
<h3>Templating Views</h3>
Can replace content inside of a template.
<pre class="prettyprint linenums"><!-- ko compose: { 
    model: 'viewComposition/inlineModule', 
    mode: 'templated' } -->
    <div data-part="header"><h1>hello world</h1></div>
    <div data-part="footer"><h1>goodbye</h1></div>
<!-- /ko -->
</pre>
Label the data-part attributes to get this, in the child views
<pre class="prettyprint linenums">// In the Child Views
<h2 data-part="header"></h2>
<h2 data-part="footer"></h2>
</pre>
