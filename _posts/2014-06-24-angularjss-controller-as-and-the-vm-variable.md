---
layout: post
title: AngularJS's Controller As and the vm Variable
date: 2014-06-24 00:27
author: John
comments: true
categories: [angular, javascript, Uncategorized]
---
<p>The great thing about coding is that we are able to mix coding style and personal/team preference together. This post is all about a preference of mine that has helped me stick to be principles of readable, efficient, and maintainable code with AngularJS.</p>

<p>It's no secret that I am a fan of the "Controller As" syntax that was revealed in AngularJS 1.2.0, in fact I wrote an <a href="http://www.johnpapa.net/do-you-like-your-angular-controllers-with-or-without-sugar/">entire post about the Controller As feature</a>. I'm also a fan of readable code and keeping things consistent and simple. We tend to spend a lot of time reading code. In fact, I bet you spend much more time reading code than you might imagine ... more-so than writing it.</p>

<p>You'll see this and more in my upcoming <a href="http://pluralsight.com">Pluralsight</a> course AngularJS Patterns: Clean Code, due out this summer 2014.</p>

<h3>vm in the HTML</h3>

<p>When I create controllers these principles apply well to the Controller As syntax. This is where I like to apply the variable <code>vm</code> for my controllers. Here is some typical code I write in HTML</p>

<pre><code>&lt;div ng-controller="Shell as vm"&gt;
  &lt;h1&gt;{{vm.title}}&lt;/h1&gt;
  &lt;article ng-controller="Customers as vm"&gt;
    &lt;h2&gt;{{vm.title}}&lt;/h2&gt;
    &lt;ul ng-repeat="c in vm.customers"&gt;
      &lt;li&gt;{{c.name}}&lt;/li&gt;
    &lt;/ul&gt;
  &lt;/article&gt;
&lt;/div&gt;
</code></pre>

<p>Notice I name the controller's instance variable <code>vm</code> in the HTML. In the MV* world, and specifically in MVVM patterns, VM represents the View's Model (aka ViewModel). But wait, this is MVC right? Meh, it's MV* .. I'm all for patterns, but I don't get hung up on conforming for the sake of conforming. So when accessing the binding scope from the controller I consider it the glue between the HTML View and the JavaScript Controller. This is the View's Model ... to to me, I like calling it <code>vm</code>. And hey, vm is short, contextual, gets the point across, and is readable.</p>

<p>Can you use anything here? Sure. In fact many examples/demos may have <code>Customers as customers</code> or <code>CustomersCtrl as customers</code>. That works fine too, but I like the short <code>Customers as vm</code> as it tells me instantly that the controller is for Customers and now I know inside my HTML I can use <code>vm</code>.</p>

<h3>Mainstream Controller As</h3>

<p>So how would it look if I used something more mainstream? Let's look.</p>

<pre><code>&lt;div ng-controller="Shell as shell"&gt;
  &lt;h1&gt;{{shell.title}}&lt;/h1&gt;
  &lt;article ng-controller="Customers as customers"&gt;
    &lt;h2&gt;{{customers.title}}&lt;/h2&gt;
    &lt;ul ng-repeat="c in customers.customers"&gt;
      &lt;li&gt;{{c.name}}&lt;/li&gt;
    &lt;/ul&gt;
  &lt;/article&gt;
&lt;/div&gt;
</code></pre>

<p>Again, this works fine, but now I have <code>customers.customers</code> in the <code>ng-repeat</code>. That's ugly and it doesn't convey that it represents controller dot array. Well, what if we call it <code>Customers as custCtrl</code> or <code>Customers as customerCtrl</code>? They work too ... and it really comes down to personal preference (of which I am not a fan of these). That's why I broke from the mainstream here.</p>

<h3>vm in the JavaScript</h3>

<p>Ah, so what does the JavaScript look like? Here I also use <code>vm</code> to represent the binding scope. This gets rid of the <code>$scope</code> variable from most of my controllers.</p>

<pre><code>angular.module('app')
    .controller('Customers', [function() {
      var vm = this;
      vm.title = 'Customers';
      vm.customers = [
        {name: 'Haley'}, {name: 'Ella'}, {name: 'Landon'}, {name: 'John'}
        ];
    }]);
</code></pre>

<p>Notice that I use <code>var vm = this;</code> and then I decorate <code>vm</code> with the members that should be exposed and data-bindable to to the View. This does 3 things for me.</p>

<ol>
<li>Provides a consistent and readable method of creating bindings in my controllers</li>
<li>Removes any issues of dealing with <code>this</code> scoping or binding (i.e. closures in nested functions)</li>
<li>Removes <code>$scope</code> from the controller unless I explicitly need it for something else</li>
<li>Makes me happy since its short :)</li>
</ol>

<p>The name <code>vm</code> here in the JavaScript does not have to match what is used in the View. So there is no coupling there other than that I like using <code>vm</code> in both.</p>

<p>One of my favorite reasons for using Controller As is that I no longer have $scope hanging around and the temptation to abuse it as a catch-all and do-everything $scope object are removed. For example, if $scope is always there as a dependency it is easier to add watches, apply, digest, on, emit, broadcast and more right in the controller. Now, they may be needed, but often I can find better ways by abstracting those to factories. So if the <code>$scope</code> is not present as a dependency, I am less tempted.</p>

<h3>Nesting Controllers</h3>

<p>One interesting aspect of this is when we nest controllers in a View. The HTML may look something like this</p>

<pre><code>&lt;div ng-controller="Shell as vm"&gt;
  &lt;h1&gt;{{vm.title}}&lt;/h1&gt;
  &lt;article ng-controller="Customers as vm"&gt;
    &lt;h2&gt;{{vm.title}} in {{$parent.vm.title}}&lt;/h2&gt;
    &lt;ul ng-repeat="c in vm.customers"&gt;
      &lt;li&gt;{{c.name}}&lt;/li&gt;
    &lt;/ul&gt;
  &lt;/article&gt;
&lt;/div&gt;
</code></pre>

<p>Notice here that the <code>vm</code> is used in both the Shell and Customers controller's HTML elements. My rule of thumb is to use <code>vm</code> until it is no longer clear (borrowed from the great <a href="https://twitter.com/wardbell">Ward Bell</a>). This might be a case for that (up to your own preferences). Both controllers have a <code>title</code> property which may be difficult to clearly identify. It is possible as shown here using the <code>$parent</code> syntax, but if you feel this is a bit to much with the <code>vm</code> here in the HTML there are other options. One of these is to clarify the <code>vm</code> as shown below.</p>

<pre><code>&lt;div ng-controller="Shell as shellVm"&gt;
  &lt;h1&gt;{{shellVm.title}}&lt;/h1&gt;
  &lt;article ng-controller="Customers as customersVm"&gt;
    &lt;h2&gt;{{customersVm.title}} in {{shellVm.title}}&lt;/h2&gt;
    &lt;ul ng-repeat="c in customersVm.customers"&gt;
      &lt;li&gt;{{c.name}}&lt;/li&gt;
    &lt;/ul&gt;
  &lt;/article&gt;
&lt;/div&gt;
</code></pre>

<p>Now we see the <code>shellVm</code> and the <code>customersVm</code> in the HTML and it is clear if we want the <code>title</code> property on either how we can get to it.</p>

<p>And remember, the JavaScript doesn't change one bit. We can still use <code>var vm=this;</code> in the Controller's JavaScript, use <code>this</code>, or call it anything we want over there.</p>

<h3>Choosing a Path</h3>

<p>Really this is a team preference that you have to decide upon. As long as you are consistent, there are many ways to skin this cat. I prefer to use <code>vm</code> (until it is not clear) and in 95% of the cases for me it's worked wonderfully clear. Choose what works for your team and enjoy coding!</p>

