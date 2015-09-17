---
layout: post
title: Web Dev with Editors and IDEs
date: 2015-04-26 15:55
author: John
comments: true
categories: [Uncategorized]
---
There are editors and IDE's (Integrated Development Environments). I've often been asked which tools I prefer, so I decided to share how I view them. Your mileage may vary on your tool selection, of course.

Influencing factors for me:

<ul>
<li>speed of the tool</li>
<li>speed of typing</li>
<li>features</li>
<li>extensibility</li>
<li>Windows and OSX</li>
<li>the "feel" and aesthetics </li>
</ul>

<h2>Differences</h2>

Editors offer super fast editing with many extension points for writing code. But first and foremost they are built for speed and they are usually highly tailored for keyboard use (not for mouse). Sublime, brackets, vim, and atom are editors.

IDE's also come with rich features including robust and top notch debugging experiences, integration with other apps, push and pull from the cloud, git, and countless other features. The upside is they can serve as a do everything tool. The downside is that IDE's can be slower, provide cognitive overload on features, and be more dependent on wizards and the mouse. Visual Studio, IntelliJ, and  WebStorm are what I classify as IDE's.

I think what really makes an IDE is the focus on making the tool be the one stop shop. There is something to be said for consolidating, but I believe there is a limit where it makes more sense for a tool to leave it to en external apparatus (ex: like terminal). There is also a case for having it be in one tool (ex: Web server code debugging).

There is a place for both. Most of the time I find myself wanting to move quickly and efficiently with the tool to write code, find my code, test it, debug it, and run it. I'd say this is 90% scenario. And for this I prefer an editor.

<h2>Experimentation</h2>

I've tried an experiment over the past 1+ year where I used Visual Studio, Atom, Brackets, WebStorm, and Sublime for a few months each. Each time I used 1 tool exclusively to force myself to see the pros and cons of each. Ultimately I learned a lot, and perhaps most of all I learned that they all are excellent and I can be productive in each of them. But I learned something about myself too ... I prefer an editor over an IDE.

<strong>Why do I prefer an editor over an IDE? Because I am more productive.</strong>

I found myself more productive with the instant startup of the editor, never having to wait for a command to open a window, process what I was asking it to do, or do one of the many things an IDE is often slow at. I love Visual Studio, but it can be slow ... just like IntelliJ or even WebStorm. I also want the tool to work great on OSX and Windows.

I highly recommend trying various tools.

<h2>Brackets</h2>

My de-facto editor (until very recently) for coding these days. Fast for coding. Love the multi-cursor and selection options. The community extensions are plentiful and robust. Built on a web browser for Web developers.

Pleasant to look at and various themes you can choose too. Yes, I like the editor I am staring at all day to look good.

Brackets has multi-cursor, tons of keyboard shortcuts, quick access to all menus, commands, files, and everything I need. What I don't have, the extensions help add to the tool.

<blockquote>
  Learn more about <a href="http://www.johnpapa.net/my-recommended-brackets-extensions/">my favorite Brackets extensions here</a>.
</blockquote>

I do not like how it is difficult to open 2 instances, and once you do open them I find many bugs where I update one instance and the other acts wonky. So for now I only use Brackets for my main coding window. When I need another, I open the second in Sublime Text.

<h2>Visual Studio Code</h2>

This is now my number 1 tool in my toolbox. Fast. Intellisense. Fast. Code hints. Fast. Debugging. Fast. Refactoring tools. Fast. Git. Huge language feature support and more ... check out my series on <a href="http://johnpapa.net/visual-studio-code">Visual Studio Code over here</a>.

<h2>Sublime Text</h2>

Super fast. In fact I use this for all text editing and quick notes. There is just about extension you could want. The tool itself is on v2 (or v3 which is still in beta and has been for a long while). However, the tool remains and the community support for it is strong.

I feel more productive in brackets, but when I just need the super fast editing for some massive sweeping changes, I sometimes come back to Sublime but it feels like an editor that just happens to be good for code, as opposed to a code editor, if that makes sense.

<h2>Atom</h2>

Fast, very similar to brackets but I personally felt more productive and comfortable in brackets. I find Atom to be slower, experienced more bugs, and had a harder time getting into it when brackets had none of those issues. Atom is also built on a web browser for Web developers.

<h2>WebStorm</h2>

I like WebStorm, but is more of an IDE than an editor. I like how it tries to make fast editing with minimal IDE features. However I think they have swayed too much on the IDE side and it most definitely slower than the true editors Brackets, Sublime, and Atom. WebStorm is certainly less of an IDE than IntelliJ (same company, much larger IDE).

It is excellent at debugging and integrating with other OSS tools like grunt, gulp, and node.  But that integration seems to come at a cost. Brackets and the editors handle most of what I need out of the box, so I rarely ever need to come over to WebStorm unless I need serious "in-tool" debugging.

Also, the appearance just feels uglier to me. Yeah, it's probably just me.

So why did I spend so much time in WebStorm if I didn't like how slow it is? because I think there is an opportunity that only WebStorm so far has explored well. Editors are awesome, but I work in many tools and the ability to integrate with them in a single environment can be highly effective. WebStorm tries to do this, most notably with the in editor debugging (as opposed to node-inspector from terminal + an open browser tab to debug the source). It needs work and they are constantly updating the features ... but the speed has still been my biggest complaint.

Also, try creating templates and snippets ... they need to be compiled down to jar files ... can you say json please?

<h2>Terminal/Console</h2>

Sure, here are many more. IntelliJ, Visual Studio, vim, textmate, eclipse, ... the list goes on and on.

The terminal (or console) are equally important to a Web developer. I prefer the out of the box OSX terminal (with a theme).

Coming from a primarily Windows world, I had been very much tied into the Visual Studio guided experience. This rarely relied on typing commands for the tool and more often was click and go (or a keyboard map). I've completely flipped on this and much prefer the keyboard to keep myself going fast. This doesn't mean I memorize commands, many of them I can create keyboard shortcuts, bash aliases, or use auto complete. But I can't deny that I am highly productive with the keyboard in terminal. I highly recommend learning your way through it.

Many of these tools offer a terminal window inside of the tool. I have used them and they work fine, but I often want multiple terminals and prefer just flipping over to a terminal window and not taking up my highly valued code window real estate. Either way, terminal is the way to go for me.

<h2>Where from here?</h2>

We are all motivated by different factors. That's why there are so many great editors and IDE's out there. I'm glad there are many options, because it different ones suit different people.

Me? I'd love to have the speed of some of these editors and a few more robust development features that you get with IDE's like WebStorm, IntelliJ and Visual Studio. The landscape is evolving, but I think the browser based tools like Atom and Brackets are the place to be for Web developers.

Pick the one(s) that suit your style.
