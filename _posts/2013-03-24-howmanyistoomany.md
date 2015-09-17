---
layout: post
title: Why All Those JavaScript Libraries?
date: 2013-03-24 16:28
author: John
comments: true
categories: [javascript, SPA, Uncategorized]
---
Flustered by so much JavaScript? Concerned with all the seemingly new patterns to learn? Confused about how to organize it? You are not alone.

<h3>Many JavaScript Libraries</h3>
You may look and think, wow, there are a lot of JavaScript libraries in this project. <a href="http://www.johnpapa.net/wp-content/uploads/2013/03/3-24-2013-11-49-54-AM.jpg" rel="attachment wp-att-16711"><img src="http://www.johnpapa.net/wp-content/uploads/2013/03/3-24-2013-11-49-54-AM-204x600.jpg" alt="3-24-2013 11-49-54 AM" width="204" height="600" class="alignright size-large wp-image-16711" /></a> The "Many" is subjective based upon your perspective. Is 3 many? Is it 10, 20, 30 ? I think it depends on who you ask. Let me put it another way: if you work on a ASP.NET MVC project take a look at all of the dll's in your references folder. How many is too many there? I bet they don't bother most folks. Rarely do I hear complaints about that. Is it because Microsoft put them there? Or is it because they are out of sight out of mind? Or possibly we are just used to them being there.

Now let's take a look at the 3rd party JavaScript libraries I included in my course and in the Hot Towel SPA template. 
<a href="http://www.johnpapa.net/howmanyistoomany/3-24-2013-11-56-52-am/" rel="attachment wp-att-16741"><img src="http://www.johnpapa.net/wp-content/uploads/2013/03/3-24-2013-11-56-52-AM.jpg" alt="3-24-2013 11-56-52 AM" width="192" height="198" class="alignleft size-full wp-image-16741" /></a>

My point is that the number of JavaScript libraries I use is dependent on the value they offer. If a library offers more value to me than me writing it, then I am fine using it.

Note that I rolled up the min versions using a feature of VS 2012. Some people remove these files, others leave them alone. Choose your own adventure :)
<pre class="prettyprint">
<Content Include="Scripts\jquery-1.9.1.js" />
<Content Include="Scripts\jquery-1.9.1.min.js">
  <DependentUpon>jquery-1.9.1.js</DependentUpon>
</Content>
<Content Include="Scripts\jquery-1.9.1.min.map">
  <DependentUpon>jquery-1.9.1.js</DependentUpon>
</Content>
<None Include="Scripts\jquery-1.9.1.intellisense.js">
  <DependentUpon>jquery-1.9.1.js</DependentUpon>
</None>
</pre>

<h3>Tracking Dependencies</h3>
I had a comment recently on a <a href="http://www.pluralsight.com/training/Courses/Discussion/single-page-apps-jumpstart" target="_blank">discussion board</a> for my latest <a href="http://jpapa.me/spajsps" target="_blank">SPA JumpStart course at Pluralsight</a>. "TheWayItIs" explains

<blockquote>My concern comes with the many code libraries and hierarchical dependencies of your patterns upon these.This in itself seems to become spaghetti of external dependencies on your patterns.</blockquote>

I already know these things, and <code>that</code> is the heart of the problem. I've gone through this jungle and come out the other end. Seeing the relationships and dependencies between these libraries is clear to me now. However, that is because I now know what to look for and how they all work together. Further, the patterns I employ help clarify this for new libraries and dependencies I may add or remove in the future. Now that I have this knowledge, it is more difficult to imagine what it is like to be without the knowledge. It is like this for anyone who tries to explain something that they know to someone who doesn't know. I have to break it back down to the time when I lacked it. This is my job: to walk through these issues and show you what to look for and how to gain this clarity. 

The dependencies are handled by 2 main players: the require.js and the module pattern. The module pattern separates code into more files, where each file has one specific role. then require.js helps load those dependencies between modules in their proper order. This is over simplification, but really, that's the key to this point: it doesn't have to be complex. 

<blockquote>Keep your code separated and let require.js handle dependencies.</blockquote>

I've been a .NET coder since the beginning and I use these same concepts with .NET. It all falls down to Single Responsibility Principle  (SRP). Keep your code separated (and do not repeat yourself) and you gain code re-use, reduce bugs, make it easier to maintain, and can scale easier. 

<h3>Production Capable?</h3>
The same person on the discussion thread at my SPA course also asks

<blockquote>... are you proposing your sessions as production capable patterns relying on these many libs or should we view these patterns as useful for an expiring app such as a code camp with speakers?</blockquote>

My answer is yes. Yes these libraries and patterns are production capable right now, today, this moment (notice the pun on moment.js). Of course patterns and libraries evolve. 

<h3>Why Introduce New Libraries?</h3>
Case in point is that I knew Durandal.js and Breeze.js were being developed when I wrote my intermediate SPA course. They were not ready for apps at that time (this was last summer), so I wrote replacements by hand. This accomplished a few things. First, when you go through my intermediate course you understand the complexities of solving these problems that these 2 libraries solve for you.  Why? Because I walked through how to do it all manually and it was much more work. Second, there is value in seeing how this all works so you do not have magical black boxes solving your issues. Not that you want to recreate the wheel, but its important to know how a wheel rolls. Finally, after going through that experience, you now understand and appreciate the value of Durandal and Breeze much more than if you had not seen how to do it all by hand.

<h3>Clarity</h3>
Clarity won't come in a heartbeat, but rest assured that it will come. Just like 100's of files in .NET appear manageable to you today, the amount of JavaScript won't appear so daunting. You'll see that many of the important patterns you know so well in .NET are still there in JavaScript. Organizing your code in .NET is slightly personal preference ... it's the same with JavaScript/HTML. You'll find the arrangement that works for you and find your chi.


These were awesome questions and they deserved some time in print. I hope they help you!
