---
layout: post
title: Route Resolve and Controller Activate in AngularJS
date: 2014-12-27 14:58
author: John
comments: true
categories: [angular, Uncategorized]
---
Angular route resolvers and controller activation. Two great options for running logic on entrance of a new View or route. I get a lot of questions about which technique to use.

<blockquote>
  I'm using AngularJS and I see 2 common patterns to retrieve data and run logic when transitioning to a new View. What's the difference between running code when a controller starts and running code in a route resolver?
</blockquote>

The key is that both are valid options. And in some cases either is fine, while in others you want to pick one over the other. They path to choosing begins with understanding the differences. The biggest difference between the 2 for a user is that <strong>resolvers happen before the route</strong> and <strong>activate happens after the route</strong>.

<h2>Code</h2>

Let's start by looking at the difference in the code between the two options.

<h3>Controller Activate</h3>

This first example shows running code on controller activation. I name the function <code>activate</code> by convention. This example is pulled directly from my Angular style guide here <a href="https://github.com/johnpapa/angularjs-styleguide#style-y080">Y080</a>.

<pre><code class="javascript">// avengers.js
function Avengers(dataservice) {
    var vm = this;
    vm.avengers = [];
    vm.title = 'Avengers';

    activate();

    function activate() {
        return dataservice.getAvengers().then(function(data) {
            vm.avengers = data;
            return vm.avengers;
        });
    }
}
</code></pre>

<h3>Route Resolve</h3>

This second code example shows running code on before a route executes. This example is pulled directly from my Angular style guide here <a href="https://github.com/johnpapa/angularjs-styleguide#style-y081">Y081</a>. This demonstrates using ngRoute but the same idea works with ui-router.

<pre><code class="javascript">// route-config.js
angular
    .module('app')
    .config(config);

function config($routeProvider) {
    $routeProvider
        .when('/avengers', {
            templateUrl: 'avengers.html',
            controller: 'Avengers',
            controllerAs: 'vm',
            resolve: {
                moviesPrepService: moviesPrepService
            }
        });
}

function moviesPrepService(movieService) {
    return movieService.getMovies();
}

// avengers.js
angular
    .module('app')
    .controller('Avengers', Avengers);

Avengers.$inject = ['moviesPrepService'];
function Avengers(moviesPrepService) {
      var vm = this;
      vm.movies = moviesPrepService.movies;
}
</code></pre>

<h2>Behavior</h2>

Now let's examine some of the ways they behave differently.

<h3>Controller Activate</h3>

<ul>
<li>The code executes after the route and in the controller's <code>activate</code> function</li>
<li>The View starts to load right away</li>
<li>Data binding kicks in when the <code>activate</code> promise resolves</li>
<li>A “busy” animation can be shown during the view transition (via <code>ng-view</code> or <code>ui-view</code>)</li>
</ul>

<h3>Route Resolve</h3>

<ul>
<li>The code executes before the route via a promise</li>
<li>Rejecting the promise cancels the route</li>
<li>Resolve makes the new view wait for the route to resolve</li>
<li>A “busy” animation can be shown before the resolve and through the view transition</li>
</ul>

I use a route resolve when I want to decide to cancel the route before ever transitioning to the View.

When I need to get data for a controller I use the controller's <code>activate</code> function. The controller activate makes it convenient to re-use the logic for a refresh for the controller/View, keeps the logic together, gets the user to the View faster, makes animations easy on the <code>ng-view</code> or <code>ui-view</code>, and feels snappier to the user. I find this to be the more common scenario, but both are valid depending on how the set of behavior fits your situation.
