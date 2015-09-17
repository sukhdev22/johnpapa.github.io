---
layout: post
title: TypeScript Modules - Part 4
date: 2013-01-21 15:46
author: John
comments: true
categories: [course, javascript, pluralsight, ravioli, typescript, Uncategorized]
---
Most every team enjoys easy to maintain and well-organized code that follows a consistent pattern (whatever that pattern may be). When developing with JavaScript it is just as important to follow a pattern to help the developer behind you, perhaps because it is so easy not to. JavaScript is a dynamic language that provide great power. But with great power comes great responsibility. Otherwise, you can easily drive right off the map. 
<h2>Ravioli Code</h2>
<a href="http://www.johnpapa.net/typescriptpost/module-ravioli/" rel="attachment wp-att-13991"><img src="http://www.johnpapa.net/wp-content/uploads/2013/01/module-ravioli-300x224.png" alt="module ravioli" width="300" height="224" class="alignleft size-medium wp-image-13991" /></a>An analogy I enjoy relates modules to ravioli. Code without modules might be strewn all over the place, tangled, hard to locate where the functionality you need lives. This is much like spaghetti code where you can't tell where one set of code begins and ends. Modules help keep code with a specific role contained within the module. This makes it easy to identify which module performs what task or service. By separating the code into modules, or ravioli, it's much easier to identify which ravioli the code you are looking for resides in.

One easy way to help maintain code re-use and organize your code is with modules. There are patterns such as the Revealing Module Pattern (RMP) in JavaScript that make this quite simple, but the good news is that in TypeScript modules become even easier with the <code>module</code> keyword (from the proposed ECMAScript 6 spec). 

<blockquote><a href="https://twitter.com/DanWahlin" target="_blank">Dan Wahlin</a> and I recently released a new course for <a href="http://pluralsight.com" target="_blank">Pluralsight</a> that focuses on providing the fundamentals to write application-scale code using TypeScript. 
<a href="http://jpapa.me/typescript101" target="_blank"><img src="http://www.johnpapa.net/wp-content/uploads/2013/01/tslogo-600x96.jpg" alt="tslogo" width="600" height="96" class="aligncenter size-large wp-image-13581" /></a>
</blockquote>

This post provides an overview on what's in the 4th module of our course. This is part 4 of 4 in an article series where I describe the different areas Dan and I feel are fundamental to learning TypeScript. You can find the other posts here:
<ul>
	<li>Part 1 - <a href="http://www.johnpapa.net/typescriptpost1/" target="_blank">Getting Started with TypeScript</a></li>
	<li>Part 2 - <a href="http://www.johnpapa.net/typescriptpost2/" target="_blank">TypeScript Grammar</a></li>
	<li>Part 3 - <a href="http://www.johnpapa.net/typescriptpost3/" target="_blank">TypeScript Classes and Interfaces</a></li>
	<li>Part 4 - <a href="http://www.johnpapa.net/typescriptpost4/" target="_blank">Modules</a></li>
</ul>
<h2>What's a Module?</h2>
If you work on a team and want to make it easier for the developer behind you, modules can certainly help with that. There are other benefits to using modules too: 
<ul>
<li>Scoping of variables (out of global scope)</li>
<li>Code re-use</li>
<li>AMD or CommonJS support</li>
<li>Encapsulation</li>
<li>Don't Repeat Yourself (DRY)</li>
<li>Easier for testing</li>
</ul>

There are others, but I think you get the point here. Can you write great code without modules? Sure! But the benefits to using modules far outweigh the learning curve. I've found that when I start a project it really helps to think about the functionality in terms of which modules I may need. It is a similar process that I use for any language, and it flows well with TypeScript.
<h2>TypeScript Modules</h2>
TypeScript categorizes modules into internal and external modules. I like to further break out the internal modules into Implicit and Named. Each are still just modules, but how you define them and use them is important. (These terms are my own, simply to help me categorize modules. You won't find them in the TypeScript spec.) For example, if you want to use AMD or CommonJS, you want to look at external modules. If you want to organize your code into files and define your own module names , then internal named modules are a good choice. 
<h2>Implicit Internal Modules</h2>
Implicit internal modules are the easiest to work with as you simply just write source code without worrying about modules. For example the following code is the entire contents of a file that defines a and creates an instance of a class in TypeScript. 
<pre class="prettyprint linenums">
class TestClass {
    private a = 2;
    public b = 4;
};
var t = new TestClass();
</pre>
There's a module in there. Do you see it? The entire set of code is in an implicit module that joins the global module / global scope / global namespace (whichever term you prefer).When you run this code you will find these variables on the window object. The point here is that you get a module out of the box as all variables are going to default tot he implicit module, the global module if you will, unless you specify otherwise.

Is this a good practice? I prefer not to go this route because it means you are putting everything in the global scope. <a href="http://oreilly.com/javascript/excerpts/javascript-good-parts/awful-parts.html" target="_blank">Global variables are bad in general</a>. However, it is important to know how your code will be treated if you ignore modules: you end up back with spaghetti. 
<h2>Named Internal Modules</h2>
When you use the <code>module</code> keyword you are using (named) internal modules. All variables defined within the module are scoped to the module and removed from the global scope. The module itself is in the global scope (though you can nest modules too). The code below shows that the <code>Rectangle</code> class and <code>rect</code> variable are both scoped to the <code>Shapes</code> module. They cannot be accessed outside of the module, which is why the final like of code would show no members of <code>Shapes</code>.
<pre class="prettyprint linenums">
module Shapes {
    class Rectangle {
        constructor (
            public height: number, 
            public width: number) {
	}
    }
    // This works!
    var rect1 = new Rectangle(10, 4);
}

// This won't!!
var rect2 = Shapes._________
</pre>
<h2>Exports</h2>
You could take that previous example and export what you want out of the module. In other words, you can make internal aspects of the module accessible outside of the module using the <code>export</code> keyword.
<pre class="prettyprint linenums">
module Shapes {
    export class Rectangle {
        constructor (
            public height: number, 
            public width: number) {
	}
    }
}
// This works!
var rect = Shapes.Rectangle(10, 4);
</pre>
You an also extend internal modules, share them across files, and reference them using the triple slash syntax. Dan and I go deeper on this topic in module 4 of our course.
<pre class="prettyprint">
///<reference path="shapes.ts"/>
</pre>
<h2>External Modules</h2>
When dealing with large JavaScript based applications it can be unwieldy to manage the sheer number of scripts you may have. The dependency chain itself can be daunting as well as knowing when to load which scripts. This is where using the AMD convention can really help. TypeScript supports AMD using external modules. This is a topic unto itself and Dan and I cover it in our course along with some recommendations on how to use it. For simple / small apps there may be no need to use AMD. But for apps that need to scale, TypeScript and AMD together can really shine. I also recommend using the <a href="http://requirejs.org/" target="_blank">require.js library</a> to help implement AMD. You can <a href="http://www.johnpapa.net/spapost6/" target="_blank">read more about require.js in my post here</a> or in <a href="http://jpapa.me/spaps" target="_blank">module titled "SPA Basics: Separating the Ravioli" of my SPA course</a>.

When using AMD (or CommonJS) and external modules, you can export an entire module and then import it into another module. This defines a dependency chain that AMD and require.js can manage for you. 
<pre class="prettyprint linenums">
// bootstrapper.ts file

// imports the greeter.ts file as the greeter module
import gt = module('greeter'); 
export function run() {
    var el = document.getElementById('content');
    var greeter = new gt.Greeter(el);
    greeter.start(); 
}
</pre>

<pre class="prettyprint linenums">
// greeter.ts file

// exports the entire module
export class Greeter { 
    start() {
         this.timerToken = setInterval(() => 
             this.span.innerText = 
             new Date().toUTCString(), 500);
    }
}
</pre>
<h2>Future</h2>
There are a lot of great features in TypeScript and it's still early. There is a <a href="http://typescript.codeplex.com/wikipage?title=Roadmap" target="_blank">roadmap that the TypeScript team has published</a> and thankfully one of the features on that list is generics. I'd love to see that addition and frankly I'd love to see the modules fleshed out even more. The tooling is just OK in my opinion, but adding in Web Essentials 2012 really improves the experience markedly for development today. They also list async/await, mixins, tooling features, and further alignment with ECMAScript 6.  I expect all of these to improve as the team approaches its full release.
