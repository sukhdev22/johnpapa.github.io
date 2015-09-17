---
layout: post
title: Angular Style Guide
date: 2014-07-29 13:23
author: John
comments: true
categories: [angular, javascript, open source, patterns, pluralsight, Uncategorized]
---
<p><img src="http://www.johnpapa.net/wp-content/uploads/2013/09/angular-icon.png" alt="angular-icon" width="96" height="96" class="alignleft size-full wp-image-21531" /> I just <a href="https://github.com/johnpapa/angularjs-styleguide">published the first draft of my opinionated style guide for syntax, conventions, and structuring AngularJS applications</a>. You'll find many of these and more explained in deeper detail in my <strong>Pluralsight course AngularJS: Clean Code</strong> (coming in August 2014). The styles contained here are based on on my experience with <a href="//angularjs.org">AngularJS</a>, presentations, <a href="http://pluralsight.com/training/Authors/Details/john-papa">Pluralsight training courses</a> and working in teams. I will keep this guide updated on github.</p>

<h2>Usage and Purpose</h2>

<p>I get asked a lot for style guides, how to get started once you learn the AngularJS basics, and what I recommend. This guide helps point in that direction using my guidelines. The purpose of this style guide is to provide guidance on building AngularJS applications by showing the conventions I use and , more importantly, why I choose them. That last part is important ... it's is not important to follow someone else's guidelines (including mine) as much as it is to understand why people choose what they do. I tried to share my reasons in this document to shed some light on how I think about the challenges and solutions. This has always helped me, and I hope it helps you.</p>

<h2>What this Guide is Not</h2>

<p>This guide is not intended to serve as a demo of reusable code, code snippets, or advanced solutions though it may drop a few here or there. Rather it is intended to be a starting point for a team looking for consistency.</p>

<h2>Community Awesomeness and Credit</h2>

<p>Never work in a vacuum. I find that the AngularJS community is an incredible group who are passionate about sharing experiences. As such, a friend and AngularJS expert Todd Motto and I have collaborated on many styles and conventions. We agree on most, and some we diverge. I encourage you to check out <a href="https://github.com/toddmotto/angularjs-styleguide">Todd's guidelines</a> to get a sense for his approach and how it compares.</p>

<blockquote>
  <p>Many of my styles have been from the many pair programming sessions <a href="http://twitter.com/wardbell">Ward Bell</a> and I have had. While we don't always agree, my friend Ward's has certainly helped influence the ultimate evolution of this guide.</p>
</blockquote>

<h2>What's Included</h2>

<p>Here is a starting list of what is included, with more to come.</p>

<blockquote>
  <blockquote>
    <p>There is much more in the <a href="https://github.com/johnpapa/angularjs-styleguide">AngularJS Style Guide</a>, which I will continue to update and add content to.</p>
  </blockquote>
</blockquote>

<ol>
<li><a href="https://github.com/johnpapa/angularjs-styleguide#single-responsibility">Single Responsibility</a></li>
<li><a href="https://github.com/johnpapa/angularjs-styleguide#modules">Modules</a></li>
<li><a href="https://github.com/johnpapa/angularjs-styleguide#controllers">Controllers</a></li>
<li><a href="https://github.com/johnpapa/angularjs-styleguide#services">Services</a></li>
<li><a href="https://github.com/johnpapa/angularjs-styleguide#factories">Factories</a></li>
<li><a href="https://github.com/johnpapa/angularjs-styleguide#directives">Directives</a></li>
<li><a href="https://github.com/johnpapa/angularjs-styleguide#resolving-promises-for-a-controller">Resolving Promises for a Controller</a></li>
<li><a href="https://github.com/johnpapa/angularjs-styleguide#manual-dependency-injection">Manual Dependency Injection</a></li>
<li><a href="https://github.com/johnpapa/angularjs-styleguide#minification-and-annotation">Minification and Annotation</a></li>
<li><a href="https://github.com/johnpapa/angularjs-styleguide#exception-handling">Exception Handling</a></li>
<li><a href="https://github.com/johnpapa/angularjs-styleguide#naming">Naming</a></li>
<li><a href="https://github.com/johnpapa/angularjs-styleguide#application-structure">Application Structure</a></li>
<li><a href="https://github.com/johnpapa/angularjs-styleguide#modularity">Modularity</a></li>
<li><a href="https://github.com/johnpapa/angularjs-styleguide#angular-$-wrapper-services">Angular $ Wrapper Services</a></li>
<li><a href="https://github.com/johnpapa/angularjs-styleguide#comments">Comments</a></li>
</ol>

<h2>Contributing</h2>

<p>If you have questions with the guide, feel free to leave them as issues in the repo. If you find a typo, create a pull request. The idea is to keep the content up to date and use github's native feature to help tell the story with issues and PR's, which are all searchable via google. Why? Because odds are if you have a questions, someone else does too! You can learn more here at about how to <a href="https://github.com/johnpapa/angularjs-styleguide#contributing">contribute</a>.</p>

