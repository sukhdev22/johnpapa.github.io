---
layout: post
title: Introducing Visual Studio Code
date: 2015-04-29 18:30
author: John
comments: true
categories: [Uncategorized]
---
Today is a pretty darn, amazing, fantastical, uber-awesome-astical-game-changing day for Web developers. Microsoft, known for its great tooling, has entered the tooling story for cross platform developers with <a href="http://code.visualstudio.com/">Visual Studio Code</a>.

Microsoft announced the launch of Visual Studio Code, a lightweight cross-platform code editor for writing modern web and cloud applications that will run on OS X, Linux and Windows at the //Build developer conference. Visual Studio Code is still officially in preview, but you can now <a href="http://code.visualstudio.com/">download it here for OSX, Linux and Windows</a>.

You can also follow Visual Studio Code on Twitter at <a href="http://twitter.com/code">@code</a>.

<blockquote>
  I'll be working on a course for Pluralsight on Visual Studio Code coming soon!
</blockquote>

If you want to see the video demo from //Build you can view it here. 
<a href="http://channel9.msdn.com/Events/Build/2015/3-680">Visual Studio Code: A Deep Dive on the Redefined Code Editor for OS X, Linux and Windows</a>

<iframe src="//channel9.msdn.com/Events/Build/2015/3-680/player" width="560" height="315" allowFullScreen frameBorder="0"></iframe>

<h2>Visual Studio Code</h2>

Visual Studio Code (VSCode) is a lightweight, super fast, cross platform development tool for building Web applications. It works well with both Node and ASP.NET v5.

<img src="http://www.johnpapa.net/wp-content/uploads/2015/04/vscode-icon-sm.png" alt="Visual Studio Code" />

<img src="http://www.johnpapa.net/wp-content/uploads/2015/04/vsc.png" alt="Visual Studio Code" />

From their download page they describe Visual Studio Code succinctly as:

<blockquote>
  Code focused development, evolved
</blockquote>

I like and agree with that statement. They go on to say the following:

<blockquote>
  Visual Studio Code is a free, modern cross-platform tool for building today's cloud and web applications
</blockquote>

That's it in a nutshell. It's fast editing experience is similar to what you get with brackets, Sublime and Atom while it's debugging and integration experience is similar to what you get with WebStorm or Visual Studio. I consider it more along the lines of an <a href="http://johnpapa.net/web-dev-with-editors-and-ides">editor than an IDE</a>, personally. But it really does fit somewhere in between, grabbing the best of both worlds.

I like VSCode because its super fast and provides some rich development features (code completion, navigation, deployment, debugging, git, task running).

More from the docs:

<blockquote>
  It is a new class of tool, one which combines the speed of today's editors with rich code authoring and debugging, without the complexity that a full IDE can sometimes present to developers. While it focuses on the core edit-compile-debug cycle, it goes beyond those basic editor scenarios by providing helpful code completion, navigation, code understanding, refactoring, diagnostics, and deployment.
</blockquote>

VSCode is folder and file based. You can open a folder and work on its files. No project file. No solution file. Just grab the code folder and go. When there is a project context, such as with ASP.NET 5, and you open a folder (with an ASP.NET 5 project), VSCode detects the project context.

<h2>Installing</h2>

Read the docs and see the links below for more details on the prerequisites and how to install and get up and running with VSCode.

<ul>
<li><a href="https://code.visualstudio.com">Get started</a></li>
<li><a href="https://code.visualstudio.com/Download">Download Visual Studio Code</a></li>
</ul>

<h2>Diving In</h2>

Follow this series to learn more about what you can do with Visual Studio Code!

<ol>
<li><a href="http://johnpapa.net/visual-studio-code">Introducing Visual Studio Code</a></li>
<li><a href="http://johnpapa.net/getting-started-with-visual-studio-code">Getting Started with Visual Studio Code</a></li>
<li><a href="http://johnpapa.net/intellisense-witha-visual-studio-code">Intellisense</a></li>
<li><a href="http://johnpapa.net/refactoring-with-visual-studio-code">Refactoring</a></li>
<li><a href="http://johnpapa.net/debugging-with-visual-studio-code">Debugging</a></li>
<li><a href="http://johnpapa.net/git-and-preferences-in-visual-studio-code">Git Integration and Preferences</a></li>
</ol>

<h2>See it in Action</h2>

Thursday April 30 Chris Dias, Erich Gamma and I will be presenting Visual Studio Code at //Build. <a href="http://www.buildwindows.com/">You can check our presentation of Visual Studio Code out at the live stream at the Build web site</a> or a <a href="http://channel9.msdn.com/Events/Build/2015/3-680">direct link here</a>. For those at Build, it is April 30, 2015 from 3:30PM to 4:30PM Day 2 Hall 1A 3-680.

<h2>What's an Editor? an IDE?</h2>

Ah, great question. But better questions might be why does this matter to me? Do you need to choose 1 tool? I explored this a bit in <a href="http://johnpapa.net/web-dev-with-editors-and-ides">this post here about editors and IDEs</a>.

<h2>What I Like</h2>

Pretty much the entire direction makes me incredibly productive. I've been using early builds for a few weeks and I'm highly productive with it already. Are there bumps? Sure, but the engineering team behind Visual Studio Code have been amazing at course correcting (they use agile iterations) super fast.

These posts outline a ton of features, but I though I'd list my top features that I am enjoying.

<h3>Top Features</h3>

<ol>
<li>Fast - I love how fast this tool is. It opens fast. I can edit fast. I can debug fast. I can navigate fast ... have I said it's fast?</li>
<li>Debugging - awesome, fast, and easy debugging of server side JavaScript and and C#</li>
<li>Intellisense - C#, TypeScript and even for JavaScript and JSON ... not to mention autocomplete and hints</li>
<li>Git integration - super helpful to be able to integrate with git, show diffs, stage, commit, clean</li>
<li>Refactoring - tons of features that make refactoring easy and fast</li>
</ol>

Awesome Runner ups ...

<ul>
<li>Task running - I can run gulp and other tasks directly from VSCode</li>
<li>Autosave - love it!</li>
<li>Go to symbol, file, task, whatever! - VSCode makes it a keystroke away to find anything you want to do</li>
<li>Customization - I can customize key bindings, tasks, editor settings - pretty much everything</li>
<li>Quick Fix - Learn <code>CMD+.</code> ... when you see a light bulb, VSCode is giving you a hint that you can refactor this, and it will offer suggestions on how!</li>
<li>Multi instance - I can open many instances and toggle between different projects</li>
</ul>

<h2>What I Miss Most</h2>

Extensions ... oh those extensions. Missing a feature? Let the community create it. But even better, open the doors to companies to create awesome extensions for VSCode that can improve integration with other tools. This feature would put it over the top. I assume this is coming. In fact, I expect it to be there.

Yes this is just one feature that is missing, but its a huge feature as it opens the doors to tons of other features.

<h2>Credit</h2>

The innovative and creative thinkers at Microsoft have really come through here. I'd be mremiss if I did not mention some of the great people who turned words into action, and made it possible to deliver Visual Studio Code working on OSX, Linux and Windows. Scott Guthrie and Scott Hunter, as the thought leaders behind ASP.NET 5 and it's much publciized cross platform approach paved the way. Erich Gamma and Chris Dias turned the idea of a cross platform top of the line development into reality.
