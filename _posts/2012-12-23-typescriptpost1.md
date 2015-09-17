---
layout: post
title: New TypeScript Fundamentals Course - Part 1
date: 2012-12-23 00:58
author: John
comments: true
categories: [course, javascript, pluralsight, typescript, Uncategorized]
---
<a href="http://www.typescriptlang.org/" target="_blank">TypeScript</a> is touted as a language for "application-scale JavaScript development". It is a typed (optionally) superset of JavaScript that compiles to JavaScript (ES3 or ES5 compliant, your choice). When Microsoft first released the preview for TypeScript, I was attracted to it because it doesn't try to invent something new. Rather, TypeScript takes JavaScript, and adds in optional static typing and a bunch of features that ES6 is looking at. So you don't have to learn something completely different. In fact, you can also <a href="http://www.johnpapa.net/debug-with-typescript08/" target="_blank">debug TypeScript either in the browser or right in Visual Studio 2012</a>!

<a href="http://www.johnpapa.net/typescriptpost1/ts/" rel="attachment wp-att-11591"><img src="http://www.johnpapa.net/wp-content/uploads/2012/12/ts.png" alt="" title="ts" width="258" height="75" class="aligncenter size-full wp-image-11591" /></a>

<h2>TypeScript Fundamentals</h2>
Over the past few months, <a href="https://twitter.com/DanWahlin" target="_blank">Dan Wahlin</a> and I have been working on a new course for <a href="http://pluralsight.com" target="_blank">Pluralsight</a> with a working title of "TypeScript Fundamentals". The course, which is due out after the holidays, focuses on providing the fundamentals you need to write application-scale code using TypeScript. The course is divided into 4 sections:
<ul>
	<li>Part 1 - <a href="http://www.johnpapa.net/typescriptpost1/" target="_blank">Getting Started with TypeScript</a></li>
	<li>Part 2 - <a href="http://www.johnpapa.net/typescriptpost2/" target="_blank">Typing, Variables, and Functions</a></li>
	<li>Part 3 - <a href="http://www.johnpapa.net/typescriptpost3/" target="_blank">TypeScript Classes and Interfaces</a></li>
	<li>Part 4 - <a href="http://www.johnpapa.net/typescriptpost4/" target="_blank">Modules</a></li>
</ul>

As the course approaches is publication in January, I'll be blogging a little about each section. This post will focus on the first section of the course. I'll post about the other sections over the next few weeks prior to the course being released.

<blockquote>UPDATE! <a href="https://twitter.com/DanWahlin" target="_blank">Dan Wahlin</a> and I just released a our new TypeScript course for <a href="http://pluralsight.com" target="_blank">Pluralsight</a>. <a href="http://jpapa.me/typescript101" target="_blank"><img src="http://www.johnpapa.net/wp-content/uploads/2013/01/tslogo-600x96.jpg" alt="tslogo" width="600" height="96" class="aligncenter size-large wp-image-13581" /></a>
</blockquote>


<h2>Getting Started with TypeScript</h2>
This section starts by discussing some of the challenges that developers face today when building applications with JavaScript. We move on to discuss how one of the goals for building application scale JavaScript is to make it more maintainable. This is where we discuss what spaghetti code is, why its not ideal, and how to move towards what we call ravioli code. Ravioli code is achieved when your code follows good separation where each set of code (each ravioli) encapsulates logic that targets a single role. In other words, each ravioli does 1 thing and 1 thing well. The raviolis do not try to perform roles that are none of their business. By separating out the raviolis, you end up with more files with easily identifiable roles, that are easily testable and maintainable.  Dan covers how TypeScript can help make it easier to bring this concept to JavaScript. 

We also discuss how JavaScript is innately a dynamic language (no static typing), which makes it harder to find errors until your run the code. TypeScript adds in optional typings which can help you identify issues before running. 

Of course the first section of this course also shows you how and where to get TypeScript, what tools you can use (there are several), and how to start writing code with it. 

<h2>Static Typing Basics</h2>
So what does TypeScript look like? The examples below show you how you can use static types to define what you will use your variables for. All you have to do is declare a variable and follow that with a colon and the type. You can then optionally initialize the variable, too. If you skip the type, TypeScript will try to infer the type for you. The variable num3 is inferred to be a number yb TypeScript, in the example below.
<pre class="prettyprint linenums">
var any1; // any value. same as not having a static type
var num1: number; // number type
num1 = 1; // set after the fact.
var num2: number = 2; // initialized and typed
var num3 = 3; //typed as a number via type inference
var str1 = num1 + 'some string';
</pre>

The next example declares a variable <code>num1</code> as a number via type inference, and sets it to 10. Then it declares <code>nothappy</code> to be a number. Finally it tries to add a number to a string and set that to a number. This is valid JavaScript, but likely is not performing the functionality that was intended by the developer. TypeScript will catch this right in the editor and tell you that it cannot convert a string to a number. This can really save you some time finding problems.

<pre class="prettyprint linenums">
var num1 = 10;
var nothappy : number;

// TypeScript alerts us there is a problem!
nothappy = num1 + 'some string'; 
</pre>

We can also define the types for parameters of function (or even of functions themselves). The <code>getArray</code> function below accepts a parameter <code>x</code> and types it as a string array. So if we try to pass in a number or a string, TypeScript will alert us right at development time in the editor. 

<pre class="prettyprint linenums">
// string array
function getArray(x: string[]) {
    var len = x[0].length;
}
</pre>

Adding types changes none of the emitted JavaScript. That's the beauty of it: it helps you write less error prone JavaScript and catch mistakes earlier.

This is only scratching the surface of what TypeScript can do for you. I'll be showing more in the upcoming posts including topics like static types, interfaces, functions, lambdas, classes, and modules. I rewrote a few JavaScript apps to now use TypeScript, and learned that there are multiple ways you can write the code and still get great results. Dan and I discuss some of those tips and learnings in the course. 

We're looking forward to putting the finishing touches on this course and hope you enjoy it!
