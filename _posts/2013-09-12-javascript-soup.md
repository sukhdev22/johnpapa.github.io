---
layout: post
title: JavaScript Soup
date: 2013-09-12 23:00
author: John
comments: true
categories: [javascript, Uncategorized]
---
Are you up an expert on <a href="http://gruntjs.com/" target="_blank">Grunt</a>, <a href="http://bower.io/" target="_blank">Bower</a>, <a href="http://www.angularjs.org" target="_blank">Angular</a>, <a href="http://knockoutjs.com/" target="_blank">Knockout</a>, <a href="http://www.durandaljs.com" target="_blank">Durandal</a>, <a href="http://www.breezejs.com" target="_blank">Breeze</a>, <a href="http://momentjs.com/" target="_blank">Moment</a>, <a href="http://www.toastrjs.com" target="_blank">Toastr</a>, <a href="http://backbonejs.org/" target="_blank">Backbone</a>, <a href="http://fgnass.github.io/spin.js/" target="_blank">Spin</a>, <a href="http://emberjs.com/" target="_blank">Ember</a>, <a href="http://facebook.github.io/react/" target="_blank">React</a>, <a href="http://www.sencha.com/" target="_blank">Sencha</a>, <a href="http://dojotoolkit.org/" target="_blank">Dojo</a>, <a href="http://getbootstrap.com/" target="_blank">Bootstrap</a>, <a href="http://purecss.io/" target="_blank">Pure</a>, and MintyZebraWaffles.js ? (Okay, that last one was made up.) But don't worry, I'd wonder about your quality of personal life if you were an expert on all of those :). But I bet you are feeling like I do sometimes where there are so many new JavaScript libraries and frameworks coming out every day (seemingly) that it's hard to keep up with. Combine that with the rate that some of the popular libraries (let's agree to call them all libraries here just for the sake of moving forward) come out with new versions is fairly frequent. No waiting years for a new version here! 

<a href="http://jpapa.me/fotoliapapa" target="_blank"><img src="http://www.johnpapa.net/wp-content/uploads/2013/09/fotolia_52214835.jpg" alt="fotolia_52214835" width="512" height="219" class="aligncenter size-full wp-image-21071" /></a>
<blockquote><a href="http://jpapa.me/fotoliapapa" target="_blank">Photo supplied by Fotolia.com.</a></blockquote>

<h2>Wading Through It All</h2>
How do you know which libraries work well together? How do you tell which libraries overlap in functionality. Sometimes you mix and match to complement each other. Other times you fill the gaps yourself. But you'd not want to use Angular with Durandal, for example. They overlap way too much and it wouldn't benefit you to use both. But you certainly could use a stack that fits well together like HotTowel which uses Durandal (soon I will release HotTowel - Angular too). 

My point here is that it can be daunting to try to keep up with everything. And while in my other posts I'll give more advice on which stacks to use, in this post I'll try to give you some insight into my warped mind on how I evaluate JavaScript libraries and wade through the JavaScript Soup.

<h2>Advice</h2>
First, I recommend you do not try to keep up with every new library. Be aware of them, sure. But you can't know everything (or at least I know I can't know everything). I personally like to be aware of what is out there and investigate ones that fill a gap or interest of mine. I use social media, newsletters, blogs, hallway chatter, and other easy to consume channels to increase my awareness. Awareness is easy, low effort. 

For example, I became aware of <a href="http://facebook.github.io/react/" target="_blank">React </a>recently. I heard it was a presentation framework like Angular, Ember, or Durandal. That alone did not interest me to go further. However, I learned the Facebook team was behind it, which caused me to have more interest in it. So I spent an hour on their site looking it over to learn what it could do and how it was different from the others. I learned enough to know it's interesting, but stuck a pin in it to come back if time ever allows. I may get back to it (knowing me I will), but I'm not worried in the meantime. If anything, I learned they have a very different perspective on SPA. if you want to <a href="http://facebook.github.io/react/blog/2013/06/05/why-react.html" target="_blank">learn more about React, check out this "Why" post</a>.

By all means, don't switch to a new library just because it is new and cool. Have some evaluation criteria that means something to you and creates a return on your investment (ROI).

<h2>Super Important</h2>
When evaluating a library, the amount of time I put into the investigation and the criteria I use depends on the risk to my application. For example, if I am looking at a presentation framework (like Angular, Durandal, or Ember) I expect more from it and will spend more time evaluating it. I'm betting my app on that library so I better be sure it's a good bet. If I am looking at spin.js or toastr.js which have very specific uses, are very small, easily swappable, and most importantly DON'T affect the critical path of my app, I'll try it out and not do as much research.

<h2>Evaluation Criteria</h3>
Here are a few categories I use to evaluate a library. There are in no particular order and are not equally weighted. You may have others, and some of these may mean little to you, so of course your mileage may vary. The key here is to choose criteria that matters to you. Here is my list:

<ul>
	<li>Quality</li>
	<li>Value</li>
	<li>Extendable</li>
	<li>Integration</li>
	<li>Stability</li>
	<li>Community</li>
	<li>Social Chatter</li>
	<li>Well Tended</li>
	<li>Documentation</li>
	<li>Owner Reputation</li>
</ul>

<h2>Quality and Value</h2>
Let's hit each of these here, starting with quality and value. If the library works as advertised, does it at a high level, and adds value to my app then I'm going to check those criteria off as positives. Point blank, the library is a tool and if the tool does its job well, I'm game. It also has to add value ... because it could be high quality but not add value. What? Think about it this way ... assume you are using ES5 and you are looking at a library that helps you create a <code>for</code> loop over an array. That may be of high quality. But it's not adding much value since you can use the ES5 array.forEach() syntax already. And if you are using ES3, you could just use a simple <code>for</code> loop. However, if the library is high quality and provides something you don't already have easily, then that adds value. Something like toastr is an example of this, where you could certainly create your own toast logic, but the time you save in using toastr adds value to me since I can spend that time on other problems (only so much time in the day).

<h2>Extendable</h2>
Can I use this library and extend its features if I want to? This is important if you like what it does but feel you may want to tweak it. This could be through a pull request on GitHub or simply by adding your own customization to it. Remember, JavaScript is inherently extendable, so it is likely that you can extend it. But make sure you can do what you need here. For example, toastr comes with basic CSS for the toasts. you may not like that CSS, so you can extend it and override it with your own. Or maybe create a plug-in for jQuery (probably the most extended library ever).

<h2>Integration</h2>
Does the library play well with others? Can I use it and library X together? This is important if you want to use, for example, Angular and Bootstrap controls. Can you? Yes. Is it easy? It depends on your definition of easy. If you are using Bootstrap with Angular it works very simply if you just use the CSS classes. If you use Bootstrap's JavaScript based controls/widgets, they work great too. But you likely want to use these two via Angular directives, to reduce the JavaScript. After all, directives are a huge selling point of Angular. So can you do this? Yes. There is a Bootstrap UI library that helps you connect these two via directives.

I get a lot of questions (100's) that are phrased like this: 
<blockquote>Can I use library X with library Y? </blockquote>

It is a great question. It is a question you should absolutely investigate if integration is important to you. To me it is very important, because I want the flexibility to use a different library and not upset the universe. You have to decide if it is important to you, and if so, investigate it for the libraries you are choosing.

<h2>Stability</h2>
Is the library stable? Does it have few breaking changes? When the breaking changes occur, do the update the version accordingly and document the changes? Hugely important questions to ask. Many libraries fail on this respect. Some of the best ones are Angular, Knockout, Durandal, and jQuery because they spend a lot of effort to make sure you don't have a bad experience.

If the library is paid, I <del datetime="2013-09-13T14:20:20+00:00">expect </del> <strong>demand </strong>this. No if, ands or buts.

<h2>Community and Social Chatter</h2>
Is there community support behind the library? Do folks watch the repo in GitHub? Do they ask questions on google groups, StackOverflow, and other social channels? Do you see folks speaking on these topics at conferences (or at least including them in their talks)? I'm not saying be a follower, but I am saying that were there is smoke, sometimes there is fire. Keep an eye on it and most importantly, learn from their experiences. You may not want to be first down the road so you can avoid the pits, but certainly don't step in those same pits when you travel that road later.

<h2>Well Tended</h2>
How often do the owners contribute to it? How often do they resolve issues? Do issues sit there forever, uncommented? A stale repo is bad news. No commits, not issues, no watchers, no pull requests could be a sign that you want to avoid that library. Be aware of it. However, just because there are a lot of activity on a repo, it doesn't mean it is awesome. So here you just want to make sure you aren't looking at an inactive library.

<h2>Reputation</h2>
What is the reputation of the team behind it? This is hugely important to me. I know that Angular, Durandal, and Knockout have great minds behind them, both which have experience in this arena. Both keep things up to date. Both know what their tools do well and stick to that plan. Both pay close attention to the community. To me, that speaks volumes. It is foolproof? No. Just because Google runs Angular doesn't mean it will be the bees knees forever. Google (like Microsoft and other big boys) also has a history of moving on. Nothing lasts forever. So if you want a library to last forever, technology is not the space for you :) 

The key here is know who makes it.

<h2>Parting Tips</h2>
You aren't the only one feeling overwhelmed. Seriously. This space is evolving fast. The answer is not to ignore it or wait til it settles down. We work in a fast paced industry. My advice is to take a step back and figure out your channels for raising your awareness and then create your evaluation criteria. I've done it and it has helped me keep from drowning :)
