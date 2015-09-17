---
layout: post
title: TypeScript Grammar - Part 2
date: 2013-01-01 16:21
author: John
comments: true
categories: [course, javascript, pluralsight, typescript, Uncategorized]
---
Finding errors earlier and more easily is one of the advantages of <a href="http://www.typescriptlang.org/" target="_blank">TypeScript</a>. You can use optionally static typed (optionally) variables, functions, objects to help detect possible mismatches in your code right in your editor. Simply add the appropriate type or define an interface for more complex and custom types, and you are off and running! Defining types is by far my favorite feature of TypeScript. 
<a href="http://www.johnpapa.net/typescriptpost2/ts-grammar/" rel="attachment wp-att-13071"><img src="http://www.johnpapa.net/wp-content/uploads/2013/01/ts-grammar.jpg" alt="ts grammar" width="599" height="181" class="aligncenter size-full wp-image-13071" /></a>

<blockquote><a href="https://twitter.com/DanWahlin" target="_blank">Dan Wahlin</a> and I just released a new course for <a href="http://pluralsight.com" target="_blank">Pluralsight</a> that focuses on providing the fundamentals to write application-scale code using TypeScript. 
<a href="http://jpapa.me/typescript101" target="_blank"><img src="http://www.johnpapa.net/wp-content/uploads/2013/01/tslogo-600x96.jpg" alt="tslogo" width="600" height="96" class="aligncenter size-large wp-image-13581" /></a>
</blockquote>


This is part 2 of 4 in an article series where I describe the different areas Dan and I feel are fundamental to learning TypeScript. You can find the other posts here:
<ul>
	<li>Part 1 - <a href="http://www.johnpapa.net/typescriptpost1/" target="_blank">Getting Started with TypeScript</a></li>
	<li>Part 2 - <a href="http://www.johnpapa.net/typescriptpost2/" target="_blank">TypeScript Grammar</a></li>
	<li>Part 3 - <a href="http://www.johnpapa.net/typescriptpost3/" target="_blank">TypeScript Classes and Interfaces</a></li>
	<li>Part 4 - <a href="http://www.johnpapa.net/typescriptpost4/" target="_blank">Modules</a></li>
</ul>
<h2>Grammar</h2>
It is easy to decorate your variables with types in TypeScript (see the image above). Start by declaring the variable and naming it (which you already do in JavaScript today). Then use the colon character and a type to indicate that this variable should be of the following type.  For example, the following code shows how you could define a variable in JavaScript which could be of any type. Then it shows how you could tell TypeScript that this variable can only be a specific type (a number). TypeScript builds on the JavaScript type system and uses the keywords number, bool, string, void, any, and null to define basic types. You can also define functions, objects, arrays, and indexers. 
<pre class="prettyprint linenums">
// Standard variable of any type using JavaScript
var age; 

// Typing "age" to a number TypeScript
var age : number; 

// Initializing the variable in TypeScript
var age : number = 99.5; 
</pre>
You may be thinking "Oh great, now I have to change all of my JavaScript to make it work in TypeScript". Fortunately that's not the case. The types are optional, so you do not have to type anything if you do not want to. For example, you could simply leave your code without annotating them with types in which case they will be of the TypeScript type <code>any</code>. Both of these examples define customer variable to be of the <code>any</code> type, which is the base type in TypeScript. 
<pre class="prettyprint linenums">
var customer; // inferred to be any

var customer : any;  // inferred to be any
</pre>
<h2>Type Inference</h2>
Let's say you copy some JavaScript over to TypeScript (put it in a *.ts file). There are no static types defined explicitly yet, however if you start hovering over some of your variables you may start to see tooltips that say your type is known to be a number or string. How can that be? This is where TypeScript uses type inference to figure out what your types are.  In the examples below, the code is valid JavaScript. If you copy that to TypeScript you and hover over the variables you will see that TypeScript is inferring their types based on how they are used! This can help TypeScript figure out if you are using a type incorrectly before you ever run it.
<pre class="prettyprint linenums">
// num1 is inferred to be number
var num1 = 1; 

// num2 is inferred to be number
var num2 = num1 + 100;

// str1 is inferred to be string
var str1 = num1 + 'some string';

// str2 is inferred to be string
var str2 = num1 + 'some string';
</pre>
Consider this next example where an object literal contains 3 properties. TypeScript is able to determine that the person variable is an object that has 3 properties with specific names and it knows what the type of each property is. It know the <code>name</code> is a string, the <code>age</code> is a number and that <code>getPets</code> is a function that return a string array. Note that all of this is valid JavaScript.
<pre class="prettyprint linenums">
// person: {name: string, age: number, getPets: () => string[] }
var person = { 
    name: 'Colleen',
    age: 25,
    getPets: function () {
        return ['Spot', 'Nemo', 'Pascal'];
    }
}
</pre>
<h2>Arrow Functions</h2>
If you have done any work with lambda expressions then arrow function expressions will look familiar. Arrow function expressions are a compact form of function expressions that have a scope of <code>this</code>. You can define an arrow function expression by omitting the <code>function</code> keyword and using the lambda syntax <code>=></code>. This allows you to write more complex function expressions as callbacks and inline functions more easily. The example below shows a simple function that accepts 2 numbers, multiples them, and return the product. The second function is equivalent, however it uses the arrow function expression syntax.
<pre class="prettyprint linenums">
var myFunc1 = function (h: number, w: number) {
    return h * w;
};

var myFunc2 = (h: number, w: number) => h * w;
</pre>
<h2>Value Proposition</h2>
Using a combination of adding explicit static types to your code and using TypeScript's type inference can help you detect problems as you write the code. The TypeScript editor in Visual Studio 2012 will alert you when it detects a problem and often direct you to the solution. For example, if you pass the wrong arguments into a function it could  tell you that it is expecting something different.  
<pre class="prettyprint linenums">
function getArrayLength(x: string[]) {
    var len = x[0].length;
    return len;
}

var names = ['John', 'Dan', 'Aaron', 'Fritz'];
console.log(getArrayLength(names))

var people = [{name: 'Aaron'}, {name: 'Fritz'}];
console.log(getArrayLength(people))
</pre>
The <code>getArrayLength</code> function below accepts and expects a string array to be passed to it and it will return a number. TypeScript defines this as <code>(x: string[]) => number</code>. The <code>names</code> variables is indeed a string array, so that will work fine. However the people array is an array of objects. TypeScript will tell you the error "Supplied parameters do not match any signature of call target". These features alone could have saved me countless hours on several web-based JavaScript applications I have worked on!
