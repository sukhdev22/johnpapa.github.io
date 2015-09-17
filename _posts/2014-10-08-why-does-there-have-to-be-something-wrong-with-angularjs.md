---
layout: post
title: Why Does There Have to be Something Wrong with AngularJS?
date: 2014-10-08 04:02
author: John
comments: true
categories: [Uncategorized]
---
<p>I've ridden deep into the trenches of JavaScript/HTML frameworks, libraries, and vanilla.js and came back out the other side. As many of you know, I have been doing a ton of AngularJS and I am enjoying it. What I have learned is that there are some great things we can do with AngularJS, and some not so great things. But I've yet to find a perfect solution and I suspect that there is no flawless approach. But that's not where I focus. Instead, I choose to look at how productive me, my teams, and the community are, the thriving ecosystem, and adoption. The bottom line is AngularJS has been tremendously productive for many people.</p>

<p>Occasionally a post is written about a technology that critiques what the author feels is entirely wrong with it. First, this is the beauty of the web: we all get to share our opinions. But we must also remember that just because we heard it on the Internet, doesn't make it the single source of truth. These opinions are interesting to read, but when the arguments are broken down the real truth usually comes out. This leads me to a recent post title <a href="https://medium.com/este-js-framework/whats-wrong-with-angular-js-97b0a787f903">What's Wrong with AngularJS</a>. In a nutshell it makes it sounds like AngularJS is a terrible option. The author criticizes declarative HTML and two-way data binding, as examples of "what's wrong", but the substance behind it (the "why") is either missing or author's preference. Some of the comments are quite interesting while others I just chuckled. Hey, preference is fine. We all have our comfy blankets but I've often found it's important when stating a case for or against something to share "why".</p>

<p>My friends <a href="http://twitter.com/danwahlin">Dan Wahlin</a>, <a href="http://twitter.com/wardbell">Ward Bell</a> and I were chatting about this and while I normally do not respond to these types of posts, but I imagine some folks may be wondering what is true and what isn't. So I want to offer some insight into my experience with Angular regarding the points the author makes, and then you can make your own decisions.</p>

<p>Without further ado, I'll explore the main points in the "what's wrong" post and share my thoughts.</p>

<h2>Declarative HTML (I think) ?</h2>

<blockquote>
  <p>App logic and structure expressed in HTML, which is enchanting for beginners (Look’ma no JS, magic!), but terrible for real development</p>
</blockquote>

<p>This is aiming at declarative development, which in Angular means directives: both built-in and custom. There is truth here: Angular is declarative. But is it terrible for real development? Why? The declarative nature works great at removing oft used features and making them simple. ngRepeat and its brothers along with semantic HTML makes my code easy to read, removes complexity I'd have to write on my own in JavaScript with selectors to interact with the DOM, and provides a common platform for teams so they can focus on the app and not the plumbing. Angular is not alone here either as Ember, Durandal and KnockoutJS are other examples that entered the declarative arena in the web with success. I have found declarative HTML to increase productivity and make it easier for teams to be more productive. But like all things, if declarative doesn't appeal to you, then another option may suit you better. It's not a bad thing to have choices: it's a good thing.</p>

<p>Can you write poorly written Angular declarative code? Certainly. But you can also write poorly written C#, Java, ASP.NET, or any other language/platform. When you break down the application needs into smaller components (whatever the technology) it becomes easier to compose reusable pieces. When you create coupled inter-dependent code, it is harder to maintain. This true of Angular just like any other tool in your belt.</p>

<p>Let's get to the real meat of this ... if you do not like Angular, then don't use it. Certain technology stokes passion in some while making others go "meh". This doesn't make it "terrible".</p>

<h2>Debugging an HTML Parser?</h2>

<blockquote>
  <p>Angular is HTML parser. I really don’t want to debug any string based parser instead of my code</p>
</blockquote>

<p>I admit, this bewilders me a bit. I don’t put JavaScript in my HTML and Angular makes it easy to avoid the temptation. I can't speak to this in detail because I don't find myself in this situation and there is nothing no detail provided to explain this in depth.</p>

<h2>Anti-Patterns?</h2>

<blockquote>
  <p>Two way databinding is an anti-pattern.</p>
</blockquote>

<p>Really? Why? What is the alternative that is better ... and why is it better? No quantitative evidence is provided that there is a real cost to data-binding that would substantiate it as an anti-pattern. if we travel this road without data binding we could take our 20 data properties and map them to HTMl elements, locating them in the DOM and stuffing them with information. Then we can pull those data values out of the elements as needed too. We can also hook up event handlers for on blur, on click, on change. It's grunt work and data-binding makes this easier, often with considerably less code. Data-binding is not the holy grail, but it qualifies as a time saver and writing less code. Less code to write equates to less code to maintain or break, too.</p>

<p>I completely disagree with the author's point entirely. But again, data-binding is a choice. A preference. If you choose not to use it, great. But it is not anti-pattern.</p>

<h2>Data-Binding</h2>

<blockquote>
  <p>While it certainly makes for a nifty demo, and works for the most basic CRUD, it doesn’t tend to be terribly useful in your real-world app</p>
</blockquote>

<p>This is from a comment about data-binding in the post. Dan and I both wrote about this and I completely disagree that it is just for demos. Why is it just for demos? What makes it be not "terribly useful"? I've written tons of code with data-binding with KnockoutJS, DurandalJS and AngularJs as well as Silverlight and WPF. Many of these apps were very large, very useful, and not very basic. Data-binding was a key part of these apps and helped reduce code, make me more productive, and light up these apps.</p>

<p>My friend Dan says it best ... and I can't improve on this as I feel exactly as he does: "If Angular went away I’d still be a fan of two-way data binding." Dan goes on further to say "I’ve gone the other route where you manually handle getting the data back into the model layer from the UI and its not fun, very brittle, and much harder to maintain." Seriously, data-binding may not be your cup of tea, and I respect that. But as long as I've been using it, it has treated me well and provided a ton of efficiencies.</p>

<h2>Dirty Checking and Object.Observe ?</h2>

<blockquote>
  <p>Dirty checking, accessors (Ember and Backbone), Object.observe and all that stuff. Wrong! It’s slow and brittle and it will consume mobile battery like hungry dog, for no reason</p>
</blockquote>

<p>The digest cycle is one place that feels like magic to some. It works in Angular and performs quite well. Can you get in trouble with it? Sure. But there are ways to avoid falling into holes, <a href="https://github.com/Pasvaz/bindonce">bindOnce</a> is a great plugin, and <a href="https://github.com/angular/angular.js/commit/2c8b4648526acf5c2645de8408a6d9ace2144b5f">AngularJS 1.3 is building in performance improvements for it</a> (checkout the <a href="https://github.com/angular/angular.js/blob/master/CHANGELOG.md">changelogs</a>, too). Even without all of those there is a lot you can do without ever worrying about the digest cycle. I feel more comfortable in a observable world, but the author also lumps that in as "wrong". So none of these leading frameworks are right? Maybe. But they solve a real problem by handling changes and responding to them. Otherwise we need to write code to do that.</p>

<p>The slow and brittle comments are not substantiated so it's hard to quantify it. When is it slow? Slower and brittler than what? What's the better approach? Not much here to go on. I'm not arguing there aren't better ways ... there almost always is a better way to do everything, but I've seen no evidence that these are "wrong".</p>

<p>I hear this type of argument a lot with mobile about pushing too much to the device and making it do too much. The mobile devices are pretty darn fast today (quad processor anyone?). Lots of data ... of course you don't want to push a ton of data down a thin wireless pipeline to a mobile device. I find I'm not pushing a lot to mobile devices and I can only display so much anyway. So if there is any cost to doing this extra processing for dirty checking on the device, it hasn't reared its head in a tangible way for me to have to consider losing the productivity that Angular brings to mobile, especially when combining it with the <a href="http://ionicframework.com">Ionic Framework</a>.</p>

<h2>Duplicated App Structure ?</h2>

<blockquote>
  <p>Duplicated app structure with obsolete angular.module.</p>
</blockquote>

<p>Angular motivates you to use modular components. It makes it easy to break things apart and decouple. So I'm not sure why this is a bad thing to create modules. I'm shaking my head at this as I type. I'm just not seeing this as a "what's wrong". This makes me think i do not understand what the author means.</p>

<p>Going further down the module road there are improvements that I'd love to see. One of which is making it easier to take a large app and load angular modules on demand. RequireJS allows us to do this as a bundle or as file by file. But often my apps are constructed in groups (or bundles) and I want to load each bundle at a time. Can I do this? Sure. But it's not straight-forward. I'm digressing just to point out that there are places where Angular can and will improve (cool stuff coming in Angular 2.0 from what the team has shared publicly already), but the author's point missed me entirely.</p>

<p>Dan writes "I’m not sure where the author is going with this point given that Angular is very modular" ... exactly, what's the point here? What else is better? You can break the app up as you please. You can decouple components. And you can even decouple from any back-end, cloud service, or 3rd party libraries to work in concert with Angular.</p>

<h2>Slow ?</h2>

<blockquote>
  <p>Angular is slow</p>
</blockquote>

<p>I used to hear this a lot, but not so much anymore. I think folks "thought" it was slow due to the digest cycle. Can it be slow? Sure, so can any code. What bottlenecks can you encounter? Perhaps 2000+ active bindings on a view (a suggested by some with experience). But we can battle that by reducing those bindings, <a href="https://docs.angularjs.org/api/ng/directive/ngModelOptions">ng-model-options</a> or even using bindOnce (or both). Look, we can make anything slow .. Ember, Knockout, React, Durandal ... but we learn how to be better at avoiding poor programming practices. hey, we all fall down, but the trick is to learn form those mistakes, not cast the tool aside and say "bad tool".</p>

<p>Slower than what? What are you doing and how are you measuring slow?</p>

<p>At best this means you can write code that is faster than what Angular does. But what are you buying by doing this? What does it cost you? Saying "slow" is the wrong way to think about it, instead we should be thinking about if we need to improve performance and what measures we can take to get there.</p>

<h2>Server-Side Rendering ?</h2>

<blockquote>
  <p>No server side rendering without obscure hacks. Never. You can’t fix broken design.</p>
</blockquote>

<p>There is absolutely not server-side rendering in Angular. Correct. There also isn't a hybrid engine or a talking dog in Angular, but I don't expect those to be there either. Angular is a client side library using Single Page Application (SPA) architecture concepts. It stays on the client and, in my opinion, thats one of the big draws to it as we get to keep the user on the client, avoid time consuming and poor user experience round trips to the server and back.</p>

<p>My best guess is that this has to be a reference to Search Engine Optimization (SEO). So let's assume that is the case. This is probably the biggest area of improvement that is begging for a better solution in the SPA space. Some companies must have SEO ready applications and it is not simple as it should be to use it with Angular. However, there are ways to tackle it such as <a href="http://prerender.io">prerender.io</a> and <a href="http://www.ng-newsletter.com/posts/serious-angular-seo.html">these techniques</a>. Google has stated they are aware of the rise of SPA (ahem, Angular) and are working on making the crawlers more aware of SPA apps. So let's call this what it is and agree SEO is far from elegant in SPA, but it is not unique to Angular.</p>

<h2>Hard to Learn ?</h2>

<blockquote>
  <p>Angular is hard to learn</p>
</blockquote>

<p>Is it? And if it is, is this unique? React, Ember, Durandal all have learning curves and who is to say one is harder than the other? That depends on your experience mostly.</p>

<p>I argue that Angular is easier to learn pound for pound for what you get out of it. Is there a lot to it? Sure. I'm still learning things about Angular, but then again I figured out most of what I needed to build apps in a week with Angular. Watch <a href="https://www.youtube.com/watch?v=i9MHigUZKEM">Dan's video on Angular in 60-minutes-ish</a> and see for yourself.</p>

<p>The author says "You have to learn a lot of Angular specific patterns useful only in Angular world. Yeah, its result of bad design. ". What's a lot? What patterns? Single Responsibility goes a long way with Angular and it certainly is not specific to Angular. Ive been doing that for years in many technologies. In fact, a huge part of my attraction to Angular is how I am able to apply many of my experiences directly to its concepts. I find there are many similarities of patterns that Java and .NET developers can make that slipstream the learning curve. DI, separation, modularity, data-binding, templating, MV* ... ? Been there. Are there new concepts? Sure ... dirty checking and the digest cycle stands out for me, but it doesn't hamper my productivity.</p>

<p>This point is all subjective.</p>

<h2>Gmail and Angular ?</h2>

<blockquote>
  <p>Google does not use Angular in production for their flag apps like Gmail or Gplus</p>
</blockquote>

<p>Maybe not but they do use it internally and also publicly in apps like AdWords or Youtube. Regardless, this is not "what's wrong". Moving along.</p>

<h2>Vendor Lock ?</h2>

<blockquote>
  <p>Vendor lock. And because Google does not use Angular in production, they can kill Angular anytime</p>
</blockquote>

<p>Sigh. I'm tired of this argument. I hear it every year about some technology. "Will X be here in 10 years?" Seriously?</p>

<p>Let's face it, we can't count on any vendor or author to support a tool forever. We always want long term support. Could they stop working on it? Sure, anything can happen. But is it likely in the near term? Heck no. And if Google did stop applying resources to Angular, what do you think would happen? Would it disappear entirely or would the OSS community pick it up? Or even another company and continue running with it? Who knows, but I don't spend my life worrying about the sky falling, personally.</p>

<p>How is any other framework proving that it will be here forever? React, Durandal, Ember, Knockout ... please.</p>

<p>All I know is that Google has a dedicated team working on Angular 1.x and Angular 2.0. Beyond that the community is thriving and building tremendous things around and integrating with Angular. It's pervasiveness, popularity and upward momentum are perhaps why it is the target of these attacks. That's kinda funny to me :)</p>

<h2>Angular 2 ?</h2>

<blockquote>
  <p>Will be rewritten entirely soon, which is a good thing for framework, but pain for you.</p>
</blockquote>

<p>This is "what's wrong" with Angular? I tend to think of evolution of a framework with a full time team working on making it better "what's right" with Angular.</p>

<p>Is there pain in upgrading to a a new version? Sure, if you upgrade. But would you? If your app is working, why upgrade? New apps won't suffer this. Existing apps should carefully consider the ROI to upgrading or staying on 1.x. Do you have pain? I don't label learning as pain, but maybe that is what the author means.</p>

<p>Angular 2 has a lot of great features and promises to address some of the difficulties, make mobile easier, improve routing, and more. There is a trade-off for using the latest and greatest. You need to weigh the cost vs benefit and decide. That's all. And this is not unique to Angular.</p>

<h2>Where Are We ?</h2>

<p>One ring to rule them all doesn't exist. We are human and we will tend to search for it, but often the "right tool for the right job" is a more productive mindset. Angular isn't perfect. Nor is any other technology option in the Web space. But it solves a problem. If it solves your problem, then stick with it. If not, choose something that does.</p>

<p><a href="https://weblogs.asp.net/dwahlin/what%E2%80%99s-%E2%80%9Cright%E2%80%9D-with-angularjs">Dan also wrote about his perspective</a>, which I highly encourage you to read too.</p>

