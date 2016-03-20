---
layout: post
title: Understanding ES5, ES2015 and TypeScript
date: 2016-03-20 01:11
author: John
comments: true
categories: [i18n, es2015, es5, es6, typescript, javascript, Uncategorized]
---

What is the difference between ES5, ES2015 (formerly known as ES6), and TypeScript? Which should we learn and use?

First, let's create a foundation for our discussion for each of these. TypeScript is a superset of JavaScript. ES2015 is the evolution of ES5. This relationship makes it easier to learn them progressively.

![ES5 to ES2015 to TypeScript](https://s3-us-west-2.amazonaws.com/johnpapa-blog-images/es5-es2015-ts.gif)

We want to understand the differences between them, but first we must understand what each of these are and why they exist. We'll start with ES5.

## ES5
ES5 is what most of us have used for years. Functional programming at its best, or worst, depending on how you view it. I personally love programming with ES5. All modern browsers support it. It's extremely flexible but also has many factors that contribute to apps that can become train wrecks. Scoping, closures, IIFE's and good guard logic are required to keep our train on the rails with ES5. Despite this, its flexibility is also a strength that many of us have leaned on.

This [chart shows the current compatibility of browsers for ES5](https://kangax.github.io/compat-table/es5/).

Perhaps the most difficult problem that ES5 poses for us is the difficulty in identifying issues at development time. Tooling for ES5 is lacking as it is complicated, at best, for a tool to decipher how to inspect ES5 for concerns. We'd like to know what properties an object in another file contains, what an invalid parameter to a function may be, or let us know when we use a variable in an improper scope. ES5 makes these things difficult on developers and on tooling.

## ES6/E2015 Leaps Forward
ES2015 is a huge leap forward from ES5. It adds a tremendous amount of functionality to JavaScript. These features address some of the issues that made ES5 programming challenging. They are optional, as we can still use valid ES5 (including functions) in ES2015.

Here are some of the ES2015 features as seen in [Luke Hoban's reference](https://github.com/lukehoban/es6features). A full list can be seen [here at the spec](http://www.ecma-international.org/ecma-262/6.0/).
- arrows
- classes
- enhanced object literals
- template strings
- destructuring
- default + rest + spread
- let + const
- iterators + for..of
- generators
- unicode
- modules
- module loaders
- map + set + weakmap + weakset
- proxies
- symbols
- subclassable built-ins
- promises
- math + number + string + array + object APIs
- binary and octal literals
- reflect api
- tail calls

This is a dramatic leap forward to ES5 and modern browsers are racing to implement all of the features. This [chart shows the current compatibility of browsers for ES2015](https://kangax.github.io/compat-table/es6/).

[Node.js](https://nodejs.org) is built against modern versions of the V8 engine. Node has implemented much of ES2015, [according to its docs](https://nodejs.org/en/docs/es6/).

> Node 4.x labels itself as Long Term Support (LTS). The LTS label indicates their release line. All even numbered major versions focus on stability and security. All odd numbered major versions (e.g. 5.x) fall under Short Term Support (STS), which focus on active development and more frequent updates. In short, I recommend you stay on node 4 for production development and node 5 for future research of features that may be in future LTS versions. You can read the [official node guidelines for versioning here](https://nodejs.org/en/blog/community/node-v5/).

Bringing it back to ES2015, we now have an incredible amount of functionality that we can optionally use to write code.

### How Do Developers Consider ES2015?
We might wonder who might be interested in ES2015 and who might not. There are many ES5 developers who are well versed in the pros and cons of the language. After over a decade in JavaScript, we may feel very comfortable with ES5. Once we master a language it can be difficult to justify leaping to a new version if we do not see the value. What are we gaining? What problem are we solving? This is a natural way of thinking. Once we decide if there is value in moving to ES2015, then we can decide to make the move.

There are also many ES5 developers who couldn't wait to use ES2015. The point is that many folks who have used ES5 are already on to ES2015, while many more are still making that decision to migrate.

There are many JavaScript developers today, but even more are coming. I believe the number now who are considering learning JavaScript and those still on their way, will dwarf that number using it today. JavaScript is growing and not everyone will have had a solid ES5 background. Some are coming from Java and C# and other popular languages and frameworks. Many of these already already have the features that ES2015 recently introduced, and have had them for years. This makes ES2015 a much easier transition for them, than ES5. And it's good timing too, as many modern browsers and Node are supporting ES2015.

So there are many of us, all with different perspectives, all leading to an eventual ES2015 (or beyond) migration.

### Supporting ES5 Browsers
How do we run ES2015 in browsers that do not yet support ES2015? We can use ES2015 and transpile to ES5 using a [tool like Babel](https://babeljs.io/). Babel makes it easy to write ES2015 (an din the future ES2016 and beyond), and still compile down to an older version of JavaScript. Pretty cool!

## TypeScript
Where does [TypeScript](http://typescriptlang.org) fit in? Should we even bother with it?

First, I think the name throws people off. The word *Type* in TypeScript indicates that we now have types. These types are optional, so we do not have to use them. Don;t believe me? Try pasting your ES5 code into the [TypeScript playground](http://www.typescriptlang.org/Playground). Look mom! No types needed! So shouldn't we optionally call it *Type?Script* or *[Type]Script* ? Kidding aside, the types are just once piece of TypeScript. Perhaps a better name is simply *ES+*.

Let's step back for a moment and revisit one of the concerns I mentioned previously that many developers have with writing JavaScript: the difficulty in identifying mistakes at development time.

What if we could identify scoping issues as we type them? What if we could identify mismatched parameters in our tool with red underlines? What if our editors and IDEs could tell us when we make a mistake in using the other people's or our own code improperly? This is what we generally rely on tooling for.

### Identifying Issues Early
Whether we use Atom, VS Code, Visual Studio, Web Storm, or Sublime Text we enjoy a plethora of innate features or extensions to our tool of choice that help us write better code faster. These tools should (and can) help use identify problems early.

Is it more fun to find an issue right away as we code it, so we can fix it there ... or to get called at 5am due to a production outage when traffic cranked up on our app and hit our hidden bug? I prefer to be home at 5 with my family :)

These tools today try their best to help identify problems, and they do an admirable job with what they have to work with. But what if we could give them a little more help? What if we could give them the same types of help that other languages like C# and Java provide today? Then these tools can really help us identify issues early and often.

This is where TypeScript shines.

The value in TypeScript is not in the writing less code. The value of TypeScript is in writing safer code. Over the long haul, it helps us to write code more efficiently as we take advantage of tooling for identifying issues and automatically filling in parameters, properties, functions, and more (often known as autocomplete and intellisense).

> You can [try out TypeScript here in their playground](http://www.typescriptlang.org/Playground).

### ES+
I joke that TypeScript should be called ES+, but when we examine it more closely, that is what is really is.

So what does TypeScript offer over ES2015? I'll focus on the three main additions I feel add the most value:

1. Types
2. Interfaces
3. Future ES2016+ features (such as Annotations/Decorators and async/await)

*TypeScript is ES plus features like these.*

Types and interfaces help provide the tooling it needs to identify problems early as we type them. With these features our editors don't have to guess whether we used a function properly or not. The information is readily available for the tool to raise a red flag to us so we can fix he issues right away. In some cases, these tools can also help recommend and refactor for us!

TypeScript promises to be forward thinking. It helps bring the agreed upon features in the future ECMAScript spec to us today. For example features like decorators (used in Angular 2) and async/await (a popular technique to make async programming easier in C#). Decorators are available now in TypeScript while async/await is coming soon in v 2.0 according to the [TypeScript roadmap](https://github.com/Microsoft/TypeScript/wiki/Roadmap).

### Is TypeScript Deviating from JavaScript?
From the top of the [TypeScript website's front page](http://www.typescriptlang.org/) we find this statement:

>TypeScript is a typed superset of JavaScript that compiles to plain JavaScript.

This is hugely important. TypeScript is not a shortcut language. It doesn't deviate from JavaScript. It doesn't take us in another direction. It's purpose is to allow us to use features in the future versions of JavaScript today, and to provide a better and safer experience.

### Why Not Just use ES2015?
That's a great option! Learning ES2015 is a huge leap from ES5. Once you master ES2015, I argue that going from their to TypeScript is a very small step. So I suggest back, once you learn ES2015, try TypeScript and take advantage of its tooling.

### What About Employability?
Does learning ES2015 or TypeScript hurt my employability? Absolutely not. But it also doesn't mean that you shouldn't understand ES5. ES5 is everywhere today. That will curve down eventually, but there is a lot of ES5 code and it's good to understand the language both to support it and to understand what problems ES2015 and TypeScript help solve. Plus we can use our knowledge of ES5 to help use debug issues using sourcemaps in the browsers.

## Keeping Up with the Emerging Technology
For a long time we didn't need transpilers. The Web used JavaScript and most folks who wrote in ES3 and ES5 used jQuery to handle any cross browser issues. When ES5 came along, not much changed there. For a long period of years in Web development we had a stable set of JavaScript features that most browsers understood. Where there were issues we used things like es5-shim.js and even jQuery to work around them. Things have changed.

The Web is moving at a fast pace. New Web standards are emerging. Libraries like Angular 2, Rx.js, React, and Aurelia are pushing the Web forward. More developers are coming to JavaScript via the web and Node.js.

The ECMAScript team is now adopting a new name for the language versions using the year as an identifier. No more ES6, now we call it ES2015. The next version is targetted as ES2016. The intention is to drive new features into JavaScript more frequently. It takes time for all browsers to adopt the standards across the desktop and mobile devices.

What does this all mean? Just when we have browsers that support ES2015, ES2016 may be out. Without help, this could be awful if we want to support all ubiquitous browsers and use the new features! Unless we have a way to use the new features today and support the browsers we need.

This is why the emergence of transpilers has become so important in the Web today. TypeScript and Babel (the major players in transpiling) both supported ES2015 before it was in the browsers. They both plan to support (and already do in some cases) ES2016 features. These tools are the current answer to how we move forward without leaving behind our customers.

### How Do We Transpile?
We can use tools like Gulp, Grunt, WebPack, and SystemJS with JSPM to transpile with Babel or TypeScript. Many editors connect directly to these tasks to transpile for us as we code. Many IDEs now support automatic transpilation with a click of a button. We can even use TypeScript from the command line to watch our files and transpile as we go.

No matter how or where we code, there are many ways to transpile.

## What It All Means
A fact in our chosen profession is that technology changes. It evolves. Sometimes it happens much faster than we can absorb it. That's why it is important to take advantage of tools that can help us absorb and adapt to the changes, like TypeScript and Babel for ES2015 (and beyond). In this case, we're using technology to keep up with technology. Seems like a paradox, but at the core it's simply using our time effectively to keep up.






