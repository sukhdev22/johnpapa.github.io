---
layout: post
title: Using Gulp in a JavaScript Build Pipeline
date: 2015-01-07 05:54
author: John
comments: true
categories: [gulp, javascript, pluralsight, Uncategorized]
---
<img src="http://www.johnpapa.net/wp-content/uploads/2014/11/gulp-2x-134x300.png" alt="gulp-2x" width="67" height="150" class="alignleft size-medium wp-image-52431" />When I can remove the friction between myself and the keyboard, it's a beautiful thing! I have more time to write code and not worry about repetitive processes. This is a key reason I love having a solid build pipeline and automated tasks in JavaScript. And my tool of choice is <a href="http://gulpjs.com">Gulp.js</a>.

Last year I published my <a href="http://www.pluralsight.com/author/john-papa">Pluralsight</a> course <a href="http://jpapa.me/ngclean">Angular Patterns: Clean Code</a> and my <a href="http://jpapa.me/ngstyles">Angular Style Guide</a>, which go together. I had a lot of folks asking for more information on using Gulp, since these materials both gave a quick glimpse of it. So I decided to release a new course with Pluralsight titled "JavaScript Build Automation with Gulp.js", due out the end of Jan 2015. Here is a glimpse of what's coming:

<ol>
<li>Requirements</li>
<li>The Value of JavaScript Task Runners (Are You Working Too Hard?)</li>
<li>The Gulp API</li>
<li>Getting Started with Gulp</li>
<li>Code Analysis and Separating Tasks from Config</li>
<li>CSS / Less Tasks and Error Handling</li>
<li>Build Task with Injection</li>
<li>Serving a Dev Build</li>
<li>Browser-Sync</li>
<li>Images and Fonts and Cleaning</li>
<li>Angular Template Caching</li>
<li>Creating and Serving a Production Build</li>
<li>Minification and Filters</li>
<li>Angular Dependency Injections</li>
<li>Static Asset Revisions and Version Bumping</li>
<li>Testing in Terminal</li>
<li>Testing in a Browser</li>
</ol>

I'm looking forward to sharing this release and hope y'all enjoy it!

In the meantime, I posted a quick primer on Gulp and the differences between Gulp and <a href="http://gruntjs.com">Grunt</a> in <a href="http://www.johnpapa.net/gulp-and-grunt-at-anglebrackets/">my Gulp/Grunt presentation here</a>.

In short, Gulp is based on streams and its based on "code over configuration'. Grunt reads files in and writes them out to disk and is based on 'configuration over code'. I find Gulp more appealing because I can read and write it faster than Grunt and it's configuration approach. Both are awesome, I use both, and it really is a team decision where you are choosing what works for your team best.
