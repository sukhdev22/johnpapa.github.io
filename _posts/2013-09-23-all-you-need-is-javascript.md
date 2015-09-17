---
layout: post
title: All You Need is JavaScript
date: 2013-09-23 20:25
author: John
comments: true
categories: [javascript, Uncategorized]
---
Is all you need JavaScript? Will writing everything yourself without helper libraries relieve the stress and get you an equally if not better solution? You may be shocked to learn that it might. And at the same time, it might not. So how do you know what to do?

Recently I wrote about <a href="http://www.johnpapa.net/javascript-soup/" target="_blank">JavaScript Soup</a>: the phrase I like to use to refer to the plethora of JavaScript libraries and frameworks that have infiltrated our daily development lives. Is turning away from libraries and writing all the code yourself in JavaScript the answer?<img src="http://piwindowonbusiness.files.wordpress.com/2011/07/chocolates-forrest-gump-1814922-397-264.jpg" width="397" height="264" class="alignright" />

<h2>Vanilla.js</h2>
First let's explore the attraction to Vanilla.js. <a href="https://twitter.com/shanselman" target="_blank">Scott Hanselman</a> pointed me to <a href="http://vanilla-js.com/" target="_blank">Vanilla.js</a>, a clever site that sheds light on the fact that you could really get all you want with plain old vanilla flavored JavaScript. The reason it's so clever is that it's so true! There is a lot we can do with JavaScript. 

Let's consider <a href="http://angularjs.org" target="_blank">AngularJS</a>, a super powerful presentation framework. Does it do anything you could not do with JavaScript? Nope. It is JavaScript. How about <a href="http://breezejs.com" target="_blank">Breeze.js</a>? Again, all JavaScript. So the argument could be made that if it's just JavaScript, why not just write it yourself. After all, you could probably do what you need in fewer lines of code, right? If you write it yourself then you won't have to learn Angular or any other library/framework! So this is always the best answer, right? Maybe.

<blockquote>If you do write an awesome bit of JavaScript code, take the next step and share it via Open Source it! If you found value, maybe someone else will too.</blockquote>

<h2>Pros and Cons</h2>
There is no panacea to web development. If we choose VanillaJS we have complete control and likely a smaller code base overall, but is it as maintainable? If we choose to use popular and stable libraries we get a lot out of the box to jump-start us and help us long-term with maintenance, but at what cost? 

The VanillaJS is appealing as you know exactly what you are getting. There is no box of <a href="http://www.youtube.com/watch?v=CJh59vZ8ccc" target="_blank">chocolates here Forrest</a>! You want to interact with the DOM, go for it. You want AJAX or promises, code them yourself. No jQuery and no other libraries. 

In some ways it's entirely empowering. When writing VanillaJS you learn more about the core of JavaScript and can really raise your expertise. The power can be intoxicating! In fact I highly recommend you give it a try if you have not. I've gone here and through that experience I learned quite a bit. 

The downside of VanillaJS is that you may be reinventing the wheel at times. You could spend a week (or even a day) writing code that already exists in a stable library. Is that bad? Not necessarily, but you need to decide the value for your time spent writing your code and then the long-term up-keep of it. Do you want to be writing cross browser code, test it in all environments, and keep it updated when something already exists? It might be more performant (yeah I know that's not a real word, but it sounds cool).

The other side is choosing a library that handles it for you. If you choose a stable library you can save those hours or days (or weeks) of coding and gain a lot of maintainability. But Are you using the library for 1% of its features and thus carrying a ton of baggage with you for features you are not using? That baggage could be in latent bugs or simply in the size of the library (think performance). You definitely need to consider this as you don't want a massive footprint in memory and size if you are not using 90%+ of it.

<h2>What Do We Do?</h2>
The picture gets a bit cloudy if you see this as an "either or" situation. But if instead of thrashing one side or the other as a global solution you consider when and where it makes sense to use each, the picture becomes much clearer.

You don't have to choose 1 or the other. Often a mixture is a good path to follow. Rarely in life do we have cut and dry decisions, and this is no exception. In my JavaScript Soup post I mention some guidelines I try to follow for choosing a library. These still apply here. If the library offers you an advantage based on that checklist and you will be using a considerable amount if its features, then feel good about using it.  

It's all about value. If you find value in it and can live with the costs, then go for it. This applies to both libraries and VanillaJS. Don't kid yourself, they both have costs. What we get paid to do is decide how to balance those costs with the project and company needs.

There is nothing wrong with using a stable library. If you can add value to your project by integrating that with some of your own VanillaJS, then go for it. That's even better!  I recommend striking a good balance between the two.

