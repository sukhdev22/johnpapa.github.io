---
layout: post
title: Browsing to a Simple Web Server on a Mac from Sublime Text
date: 2013-10-18 14:37
author: John
comments: true
categories: [javascript, mac, sublime, Uncategorized]
---
<img src="http://www.johnpapa.net/wp-content/uploads/2013/10/sublime.jpg" alt="sublime" width="160" height="160" class="alignleft size-full wp-image-21981" />Lately one of the computers I have been using is a Mac Air with the Haswell chip. The combination of the Mac Air's sleek and lightweight design along with the super long life and power of the Haswell chip is just fantastic!  I'm using both OSX and Windows (in Parallels) and I spend most of my time on the Air in Xcode, <a href="http://www.sublimetext.com/" target="_blank">Sublime Text</a>, and Visual Studio (also tinkering with <a href="http://www.jetbrains.com/objc/" target="_blank">AppCode from Jet Brains</a> ... but more on that later). 

When I want to write and test some quick HTML/JavaScript/CSS that requires a web server on the Mac Air I use Sublime Text. Sublime is pretty cool as an editor and the plug-in ecosystem is reach. But many of the plug-ins lack polish, some don't seem to work well, and it can be daunting to know which one to choose at times. Overall I love the plug in model, but its very similar to Visual Studio's in that you need to try them out to know which you like. So why did I go down this road? Well, when writing and testing some SPA code I often want to run it in the context of a web server. Simple HTML/JS is fine off the file system, but somethings require a bit more. For example, to avoid getting Cross Origin request errors when using <a href="http://angularjs.org" target="_blank">AngularJS</a> and routing for templates.

I found a quick and easy way to solve this with some built in OS features on the Mac.

<h3>Browsing from Sublime</h3>
I wanted to browse HTML code without a web server on a Mac. So i could simply right click the HTML file in Sublime and open it in the browser and have it point to localhost on a specified port (and not <code>file://</code>)

Why? If you open a HTML file in the browser from Sublime it may run, but it also may produce an error about cross origin request if your code has any of that (like with routing of templates). This is because you may be serving everything off the file system and not a web server.

<h3>Quick Solution</h3>
Run the SimpleHTTPServer on the Mac using the Terminal, for the folder where your code lives.

<ul><li><code>CMD + SPACE</code> (open Spotlight)</li>
<li>Type <code>Terminal</code> and hit <code>ENTER</code></li>
<li>Navigate to your development folder.</li> 
<li>Type <code>python -m SimpleHTTPServer 8000</code></li>
<li>Right click in Sublime and Open in Browser</li>
</ul>

This should browse to your code at <code>http://localhost:8000/SublimeTest/index.html</code>

I made some assumptions here. For example, when you navigate to your development folder, I put all my demos under the same folder to make life easy. My folder is called <code>develop</code>, so this is where I set up the server. 



<blockquote>Thanks to Ward Bell and Jesse Liberty to helping test this with me.</blockquote>






