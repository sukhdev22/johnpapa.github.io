---
layout: post
title: Preparing for Animations in Angular 1.2.0
date: 2013-08-15 01:47
author: John
comments: true
categories: [angular, animation, javascript, SPA, Uncategorized]
---
This week <a href="http://blog.angularjs.org/" target="_blank">Angular 1.2.0 rc1 was released</a> and its jam-packed with goodness. You can check out the <a href="http://code.angularjs.org/1.2.0rc1/docs/api" target="_blank">release notes</a> and <a href="https://github.com/angular/angular.js/blob/master/CHANGELOG.md" target="_blank">change log here</a>. There are a lot of improvements over the previous stable release. If you have been using the "unstable" branches such as 1.1.5, be aware that there are a few breaking changes. One of those is in the use of the new animations feature, which I'll discuss here. 

If you want to <a href="http://plnkr.co/edit/b1hoRXBreMMi6zIuQXr2" target="_blank">jump right to an example, click on this plunker</a>, then come back for the explanation. I'll have more animation examples in my upcoming course at <a href="http://ww.pluralsight.com" target="_blank">Pluralsight</a> on using Angular and Breeze to build a powerful SPA.

<blockquote>Special thanks to Matias Niemelā of the Angular team for helping me test the features. And more importantly, for his great animations work on the <a href="http://www.yearofmoo.com" target="_blank">yearofmoo</a>.</blockquote>

<h2>Cheat Sheet</h2>
Here are the directives that support animations <a href="http://ci.angularjs.org/job/angular.js-angular-master/lastSuccessfulBuild/artifact/build/docs/api/ngAnimate" target="_blank">(see the docs for more details)</a>.
<ul><li><code>ngRepeat</code> enter, leave and move</li>
<li><code>ngView</code> enter and leave</li>
<li><code>ngInclude</code> enter and leave</li>
<li><code>ngSwitch</code> enter and leave</li>
<li><code>ngIf</code> enter and leave</li>
<li><code>ngClass</code> add and remove</li>
<li><code>ngShow</code> & <code>ngHide</code> add and remove (the ng-hide class value)</li>
</ul>

<h2>Conventions</h2>
The convention for using the animations is to define the starting and termination animations using a naming convention. For example, let's create an animation that fades in and fades out for <code>ng-include</code> with an animation called <code>fader-animation</code>. Then we'll add its starting and terminating states.

Here is how we will apply the animation once we write it.
<pre class="prettyprint linenums">
    <div ng-include="'/app/views/myview.html'"
         ng-class="fader-animation"></div>
</pre>

And now we create the CSS for the fader-animation.

<pre class="prettyprint linenums">
// Starting animation for enter
.fader-animation.ng-enter
// Terminating animation for enter
.fader-animation.ng-enter.ng-enter-active
// Starting animation for leave
.fader-animation.ng-leave
// Terminating animation for leave
.fader-animation.ng-leave.ng-leave-active
</pre>
When Angular sees a class defined along with one of the supported directives from the above cheat sheet, it will add the styles for them. In the case of <code>ng-include</code>, it will add <code>ng-enter</code>, <code>ng-enter-active</code>, <code>ng-leave</code>, and <code>ng-leave-active</code> at the appropriate times.

Once we define these we can mix them up to create a simple fader animation. First, define the transitions for the animations. This says we want to transition for all supported CSS properties using a cubic-bezier easing for a duration of half a second.
<pre class="prettyprint linenums">
.fader-animation.ng-enter,
.fader-animation.ng-leave {
    -webkit-transition: all cubic-bezier(0.250, 0.460, 0.450, 0.940) 0.5s;
    -moz-transition: all cubic-bezier(0.250, 0.460, 0.450, 0.940) 0.5s;
    -o-transition: all cubic-bezier(0.250, 0.460, 0.450, 0.940) 0.5s;
    transition: all cubic-bezier(0.250, 0.460, 0.450, 0.940) 0.5s;
}
</pre>
Next we set the starting and terminating states of the animations. When the template enters we want it to have an opacity of 0. When it has finished entering, its opacity should be 1. 
<pre class="prettyprint linenums">
.fader-animation.ng-enter {
    -ms-opacity: 0;
    opacity: 0;
}
.fader-animation.ng-enter.ng-enter-active {
    -ms-opacity: 1;
    opacity: 1;
}
</pre>
When the template starts to leave we want it to have an opacity of 1. When it has finished leaving, its opacity should be 0. 
<pre class="prettyprint linenums">
.fader-animation.ng-leave {
    -ms-opacity: 1;
    opacity: 1;
}
.fader-animation.ng-leave.ng-leave-active {
    -ms-opacity: 0;
    opacity: 0;
}
</pre>
<h2>Converting from the ngAnimate Directive</h2>
If you have used the <code>ngAnimate</code> directive in Angular 1.1.5, then you'll want to make sure you read this section and the docs on what has changed with them. 
<ul>
	<li>ngAnimate directive</li>
	<li>ngAnimate module</li>
	<li>Conventions</li>
</ul>
Angular, like some other libraries, is moving towards a modular structure. This is emerging more in 1.2.0 with several modules being broken out, including <code>ngSanitize</code>, <code>ngRoute</code>, and <code>ngAnimate</code>. That's right, <code>ngAnimate</code> is now a module in a separate file that you can include or exclude.
<pre class="prettyprint">
// create the app module, and declare
// that it depends on the ngAnmiate module
angular.module('app', ['ngAnimate']);
</pre>
You'll want to go grab the file from the Angular site. Just click the Download button, then Unstable (for v1.2.0), and the Extras link to see the available modules.

You may also notice that the <code>ng-animate</code> directive is no longer used. It was in the unstable branch, so you'd only have hit this if you were using it like I was. So what happened? You can now put the CSS class right in a <code>class</code> attribute or the <code>ng-class</code> directive. 

Finally, the naming conventions have changed. I won't go into what they were, since it was in the unstable branch. But if you already have animations, you will want to use the conventions I show at the beginning of this post.

<h2>Upgrade Tips</h2>
It did not take me long to upgrade my code from 1.1.5 to 1.2.0 rc1, however I did hit some problems with the animations. First, the enter transitions were not working for me in all cases with <code>ng-include</code> and <code>ng-view</code>. Long story short, the Angular team is aware of this and a fix is already planned for 1.2.0 rc2. No errors occurred,the enter transitions simply were not firing due to how the DOM was being changed.

Another issue I ran into was with the <code>ui-view</code> directive from <a href="https://github.com/angular-ui/ui-router" target="_blank">the ui-router project</a>. UI-Router is an alternative router you can use with Angular that also supports state. It does not yet support the new animations in 1.2.0, though I expect it will in the near future. I reiterate this only affects UI-Router. The Angular router and <code>ng-view</code> do work with the animations as shown in the 1.2.0 docs.

If you are using the show and hide animations then you'll want to pay attention to the tips on the Angular site about creating a CSS class for <code>ng-hide</code> yourself that sets <code>display:none</code>. They recommend creating it very early in your page for your entire SPA so that it is ready right away. This is important because you may have animations running right after startup in a race with Angular starting up. For more details, i recommend checking out the docs on this. Without it, my hide and show animations were showing then removing themselves at startup. With it, they started invisible, which is what I wanted.

<h2>More Angular and SPA</h2>
If you love SPA you should definitely check out the upcoming AngleBrackets conference in Las Vegas Oct 26-30. I'll be hosting a full day workshop on SPA and presenting there on 2 great SPA frameworks: Angular and Durandal. My good friend Dan Wahlin is also presenting a few Angular sessions as well. Scott Hanselman, Douglass Crockford, Scott Guthrie, and many more will be there too! The event is co-located with DevIntersection, and one ticket gets you into both events. Better yet, you can <a href="https://www.anglebrackets.org/register.aspx" target="_blank"><strong>register now with the code <code>PAPA</code> and get a $50 discount</strong></a>! I hope to see you there!

