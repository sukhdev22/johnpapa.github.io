---
layout: post
title: TypeScript Classes and Interfaces - Part 3
date: 2013-01-07 03:38
author: John
comments: true
categories: [course, javascript, oop, pluralsight, typescript, Uncategorized]
---
It's likely that you've used classes and interfaces in statically typed languages to organizing your code into logical units. When you work with JavaScript these constructs do not exist, so we use the excellent replacements like constructor functions and the module pattern. However, you may still miss classes and interfaces (which play together quite nicely) and if so, you may want to take a closer look at <a href="http://www.typescriptlang.org" target="_blank">TypeScript</a>. Classes are being discussed for the next ECMAScript 6 revision, and as such, TypeScript has taken them under its wing. 
<a href="http://www.johnpapa.net/typescriptpost3/typescript-classes/" rel="attachment wp-att-13381"><img src="http://www.johnpapa.net/wp-content/uploads/2013/01/typescript-classes.jpg" alt="typescript classes" width="600" height="331" class="aligncenter size-full wp-image-13381" /></a>

<blockquote><a href="https://twitter.com/DanWahlin" target="_blank">Dan Wahlin</a> and I just released a new course for <a href="http://pluralsight.com" target="_blank">Pluralsight</a> that focuses on providing the fundamentals to write application-scale code using TypeScript. 
<a href="http://jpapa.me/typescript101" target="_blank"><img src="http://www.johnpapa.net/wp-content/uploads/2013/01/tslogo-600x96.jpg" alt="tslogo" width="600" height="96" class="aligncenter size-large wp-image-13581" /></a>
</blockquote>


This post should give you a primer on what's in the 3rd module of our course (where we cover classes and interfaces in depth). This is part 3 of 4 in an article series where I describe the different areas Dan and I feel are fundamental to learning TypeScript. You can find the other posts here:
<ul>
	<li>Part 1 - <a href="http://www.johnpapa.net/typescriptpost1/" target="_blank">Getting Started with TypeScript</a></li>
	<li>Part 2 - <a href="http://www.johnpapa.net/typescriptpost2/" target="_blank">TypeScript Grammar</a></li>
	<li>Part 3 - <a href="http://www.johnpapa.net/typescriptpost3/" target="_blank">TypeScript Classes and Interfaces</a></li>
	<li>Part 4 - <a href="http://www.johnpapa.net/typescriptpost4/" target="_blank">Modules</a></li>
</ul>
<h2>Do I Need Classes?</h2>
I generally consider 3 main conditions where I consider a class, regardless of the language. 
<ul><li>Creating multiple new instances</li>
<li>Using inheritance</li>
<li>Singleton objects</li></ul>
There are others, but let's look at these 3. For singletons I could just as easily use the Module Pattern, and frankly I generally do that with TypeScript. For creating instances, classes are nice but they are not necessary in JavaScript either. 

Let me be clear that classes are pretty awesome, but it's not like we can't do these things in JavaScript today using other techniques. The reason TypeScript's classes are valuable is not because you can't do them today, it's because they make it so much easier to do these things. If you want an example, try to write your own class structure that uses inheritance in JavaScript. 


<blockquote>If you take anything out of this post, take this: TypeScript makes it easier to write structured code, and part of that is using classes.</blockquote>


<h2>Creating a Class</h2>
You can create a class and even add fields, properties, constructors, and functions (static, prototype, instance based). The basic syntax for a class is as follows:

<pre class="prettyprint linenums">
// TypeScript
class Car {
    // Property (public by default)
    engine: string;

    // Constructor 
    // (accepts a value so you can initialize engine)
    constructor(engine: string) {
        this.engine = engine;
    }
}  
</pre>
This code creates a Car class that has a constructor that accepts a single parameter <code>engine</code> that initializes the instance property with the same name. so we can write 
<pre class="prettyprint">
var hondaAccord = new Car('V6');
</pre>
The <code>engine</code> property is defined as being public (public is the default). We could have simply put the public keyword there too. The property could be made private by prefixing the definition with the keyword <code>private</code>. Inside the constructor the <code>engine</code> property is referred to using the <code>this</code> keyword. This code emits this JavaScript:
<pre class="prettyprint linenums">
// JavaScript
var Car = (function () {
    function Car(engine) {
        this.engine = engine;
    }
    return Car;
})();
</pre>
<h2>Functions</h2>
You can create a function on an instance member of the class, on the prototype, or as a static function. Often you will want to use the prototype for the functions on classes if you intend to create multiple instances of the object. Why? Because the prototype can save you some memory as it only exists once while creating a function on every instance of the class would create 1 function per instance. Creating a function on the prototype is easy in TypeScript, which is great since you don;t even have to know you are using the prototype.
<pre class="prettyprint linenums">
// TypeScript
class Car {
    engine: string;
    constructor (engine: string) {
        this.engine = engine;
    }

    start() {
        return "Started " + this.engine;
    }
} 
</pre>
Notice the <code>start</code> function in the TypeScript code. Now look at the emitted JavaScript below, which defines that <code>start</code> function on the prototype.
<pre class="prettyprint linenums">
// JavaScript
var Car = (function () {
    function Car(engine) {
        this.engine = engine;
    }
    Car.prototype.start = function () {
        return "Started " + this.engine;
    };
    return Car;
})();
</pre>
But if you want to create a function as an instance member, you can do so like this:
<pre class="prettyprint linenums">
// TypeScript
class Car {
    engine: string;
         stop: () => string;
    constructor (engine: string) {
        this.engine = engine;
        this.stop = () => "Stopped " + this.engine;
    }

    start() {
        return "Started " + this.engine;
    }
}
</pre>
One way to create a function like this is to do it in the constructor. The emitted JavaScript now shows that the start function is on the prototype and the stop is an instance function. It's not a great design to mix these, your better off picking one or the other.
<pre class="prettyprint linenums">
// JavaScript
var Car = (function () {
    function Car(engine) {
        var _this = <span class="hiddenGrammarError" pre="var ">this;
        this</span>.engine = engine;
        this.stop = function () {
            return "Stopped " + _this.engine;
        };
    }
    Car.prototype.start = function () {
        return "Started " + this.engine;
    };
    return Car;
})();
</pre>
<h2>Inheritance</h2>
Class inheritance, as you are probably familiar with it, is not is not something you'd want to hand code in JavaScript. This is an area that TypeScript clearly shines brightly. For example, you can define an <code>Auto</code> class and then define a <code>ManlyTruck</code> class that inherits from <code>Auto</code>. This would provide access to all the public members and the constructor to the <code>ManlyTruck</code> class. It can refer to the base class using the <code>super</code> keyword and it can extend the definition by adding its own members.
<pre class="prettyprint linenums">
// TypeScript
class Auto {
    engine: string;
    constructor(engine: string) {
        this.engine = engine;
    }
} 

class ManlyTruck extends Auto {
	bigTires: bool;
    constructor(engine: string, bigTires: bool) {
        super(engine);
        this.bigTires = bigTires;
    }
}
</pre>
TypeScript emits JavaScript that helps extend the class definitions, using the <code>__extends</code> variable. This helps take care of some of the heavy lifting on the JavaScript side.
<pre class="prettyprint linenums">
var __extends = this.__extends || function (d, b) {
    function __() { this.constructor = d; }
    __.prototype = b.prototype;
    d.prototype = new __();
};
var Auto = (function () {
    function Auto(engine) {
        this.engine = engine;
    }
    return Auto;
})();
var ManlyTruck = (function (_super) {
    __extends(ManlyTruck, _super);
    function ManlyTruck(engine, bigTires) {
        _super.call(this, engine);
        this.bigTires = bigTires;
    }
    return ManlyTruck;
})(Auto);
</pre>
<h2>Interfaces</h2>
One of the coolest parts of TypeScript is how it allows you to define complex type definitions in the form of interfaces. This is helpful when you have a complex type that you want to use in your application such as an object that contains other properties. For example, we could define an interface for a Car class such that every car must have an engine and a color like this.
<pre class="prettyprint linenums">
// TypeScript
interface ICar{
    engine: string;
    color: string;
}

class Car implements ICar {
    constructor (public engine: string, public color: string) {
    }
} 
</pre>
The <code>Car</code> class adheres to the interface <code>ICar</code> because it <code>implements</code> <code>ICar</code>. You can use interfaces on classes but you can also use them to define regular variables types. Notice the code below defines the <code>toyotaCamry</code> variable to use the type <code>ICar</code>.
<pre class="prettyprint">
// TypeScript 
var toyotaCamry : ICar;
</pre>
This <code>Car</code> sample also uses the alternate syntax in the constructor to define that not only are the <code>engine</code> and <code>color</code> parameters being passed to the constructor but they are also defining a public member of the Car class. This is a nice shortcut syntax since you don;t have to define the members nor set them in the constructor: it does this for you, as you can see in the emitted JavaScript.
<pre class="prettyprint linenums">
// JavaScript
var Car = (function () {
    function Car(engine, color) {
        this.engine = engine;
        this.color = color;
    }
    return Car;
})();
</pre>
<h2>Structure</h2>
I can see developers who are familiar with Object Oriented Programming (OOP) feeling very comfortable with TypeScript's classes and interfaces. There is a lot of value here in getting running quickly and feeling secure that you have written solid code. There is so much more that classes and interfaces can do too, as Dan and I show in our TypeScript course at Pluralsight.
