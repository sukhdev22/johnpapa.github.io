---
layout: post
title: Angular and Gulp
date: 2015-02-09 12:31
author: John
comments: true
categories: [angular, gulp, javascript, pluralsight, Uncategorized]
---
<img src="http://www.johnpapa.net/wp-content/uploads/2014/11/gulp-2x-134x300.png" alt="gulp-2x" width="67" height="150" class="alignleft size-medium wp-image-52431" />Streamlining Angular code is sublime. We can streamline the process of optimizing <a href="http://angularjs.org">Angular</a> apps for dependency injections, template caching, and common JavaScript optimizations such as minification, all in preparation for production using build automation tools like <a href="http://gulpjs.com">Gulp.js</a>. Gulp is based on streams follows the mantra of "code over configuration'.

<a href="http://jpapa.me/gulpps"><img src="http://www.johnpapa.net/wp-content/uploads/2015/02/gulpps-600x110.png" alt="gulpps" width="600" height="110" class="aligncenter size-large wp-image-57601" /></a>

My new course <a href="http://jpapa.me/gulpps">JavaScript Build Automation with Gulp.js</a> was just released on Pluralsight. You can learn how to make your JavaScript do tricks and develop more efficiently, using Gulp in this course. In this course I take you from learning what Gulp does, how to install it on both Windows and a Mac, to building an entire build pipeline step by step. I spend a lot of time explaining why each step exists and what the value of the Gulp tasks are.

<h2>Angular Template Caching</h2>

One example of how to streamline your Angular app is to let Gulp do the work of taking your HTML templates and pushing them into the Angular $templateCache service. This means that the templates for your directives and views, for example, will not need to make an extra HTTP call to get each template.

Let's explore how this works in Angular first. When a directive executes it will need its template. Angular first checks the $templateCache to see if the template exists in there. The $templateCache is a dictionary of entries, keyed by the url of each template. If the template exists in the cache, it will provide it to the directive. If it does not exist, it will go to the url over HTTP and retrieved the template, stick it in the cache, and provide it to the directive. We can save a lot of HTTP traffic for directives if we stuff these templates into the $templateCache in advance. This is effectively priming the cache.

Where does Gulp step in? It is ideal for automating tasks like this as it can go through all of our code and determine what to stuff into the cache, generate a file that contains the Angular code to stuff the $templateCache, and customize it to add it to an existing module or create a new stand alone module. Gulp uses the <code>gulp-angular-templatecache</code> plugin to do the work here.

Here is a code snippet from the course:

<pre><code class="javascript">// Gulp task for creating template cache
gulp.task('templatecache', function() {
    log('Creating an AngularJS $templateCache');

    return gulp
        .src(config.htmltemplates)
        .pipe($.minifyHtml({empty: true}))
        .pipe($.angularTemplatecache(
            config.templateCache.file,
            config.templateCache.options
        ))
        .pipe(gulp.dest(config.temp));
});
</code></pre>

First I provide the source files to gulp, which are the html templates in my project. Then I minify the HTML (leaving empty tags alone in case they are needed). Why minify the HTML? Why not? Saving any bytes can be helpful.

Next the template cache runs through the code an creates a file named <code>templates.js</code> in a temp folder. My index.html looks for the templates in that folder. Later I will optimize all of the JavaScript, but for now this does nicely.

I use config variable settings for all of my file paths. I find this makes it much easier to modify the file for multiple projects.

<pre><code class="javascript">// Path settings for Gulp
var clientApp = './src/client/app/';
var config = {
    htmltemplates: clientApp + '**/*.html',
    templateCache: {
        file: 'templates.js',
        options: {
            module: 'app.core',
            root: 'app/',
            standAlone: false
        }
    },
    temp: './.tmp/'
};
</code></pre>

here is an example of what the $templateCache looks like (with ... replacing the HTML and some formatting I added for readability):

<pre><code class="javascript">angular
    .module("app.core")
    .run(["$templateCache", function($templateCache) {
        $templateCache.put("app/dashboard/dashboard.html","&lt;section&gt; ... &lt;/section&gt;");
        $templateCache.put("app/layout/ht-top-nav.html","&lt;nav&gt; ... &lt;/nav&gt;");
        $templateCache.put("app/widgets/widget-header.html","&lt;div&gt; ... &lt;/div&gt;");
    }]);
</code></pre>

This is just one example showing how you can add value to your development efforts using Gulp!

<h2>What Else is in the Course</h2>

Here is a brief outline of the course:

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
<li>First Look at Gulp 4</li>
</ol>
