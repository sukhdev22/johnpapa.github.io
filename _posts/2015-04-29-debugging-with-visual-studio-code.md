---
layout: post
title: Debugging with Visual Studio Code
date: 2015-04-29 18:34
author: John
comments: true
categories: [Uncategorized]
---
There are various ways you can debug server side code with VSCode. You may have a simple node server to crank up. Perhaps you use TypeScript and need to compile it to JavaScript before starting the server. You may also be using task automation with gulp or grunt and want to start the server and then attach VSCode's debugger to it.

<h2>Visual Studio Code Series</h2>

Follow this series to learn more about what you can do with Visual Studio Code!

<ol>
<li><a href="http://johnpapa.net/visual-studio-code">Introducing Visual Studio Code</a></li>
<li><a href="http://johnpapa.net/getting-started-with-visual-studio-code">Getting Started with Visual Studio Code</a></li>
<li><a href="http://johnpapa.net/intellisense-witha-visual-studio-code">Intellisense</a></li>
<li><a href="http://johnpapa.net/refactoring-with-visual-studio-code">Refactoring</a></li>
<li><a href="http://johnpapa.net/debugging-with-visual-studio-code">Debugging</a></li>
<li><a href="http://johnpapa.net/git-and-preferences-in-visual-studio-code">Git Integration and Preferences</a></li>
</ol>

<h3>Debugging JavaScript</h3>

You can debug server side JavaScript in right in VSCode. Just create a debug launch task and go. First, click on the debug icon in the sidebar or <code>CMD+SHIFT+D</code>. Then click on the gear icon next to the debug button in the upper left. This opens the debug configuration settings (in <code>.settings/launch.json</code>).

<img src="http://www.johnpapa.net/wp-content/uploads/2015/04/js-debug0.png" alt="js-debug0.png" />

Here you can define a launch configuration for debugging. Notice the type is set to node and the <code>program to start</code> is set to <code>/src/server/app.js</code> (choose your path accordingly). It will also stop upon entry, so you can debug on the first entry point to the <code>app.js</code>. This is important when you want to see how the node server is being started.

Once the debug configuration is established you can choose your configuration form the dropdown and click the green button, or alternatively press <code>F5</code> to begin debugging.

<img src="http://www.johnpapa.net/wp-content/uploads/2015/04/js-debug1.png" alt="js-debug1.png" />

The node server will start and stop at the first line of code in <code>app.js</code>. You can then set watchers, breakpoints (or disable them), see the call stack, or examine local variables.

<h3>Debugging Menu Options</h3>

You can also step through the code using the debug menu in the top middle of VSCode.

<img src="http://www.johnpapa.net/wp-content/uploads/2015/04/js-debug2.png" alt="js-debug2.png" />

The buttons have keyboard mappings for:

<ul>
<li><code>F5</code> continue</li>
<li><code>F10</code> step over</li>
<li><code>F11</code> step into</li>
<li><code>SHIFT+F11</code> step out</li>
<li><code>SHIFT+F5</code> stop</li>
</ul>

<blockquote>
  I often will set breakpoints in my routes and then go use the app in the browser. When the route is hit, the browser will wait and VSCode will show the breakpoint. This workflow is ideal for debugging calls between the browser and the server.
</blockquote>

<h3>Debugging TypeScript</h3>

Debugging TypeScript is just as easy as JavaScript.

<ul>
<li>Go to the debug configurations ( <code>CMD+SHIFT+P</code> and type <code>debug config</code> )  </li>
<li>Set the <code>program to start</code> to <code>/src/server/app.ts</code> (or whatever your path is)</li>
<li>Run the <code>Launch app.ts</code> configuration </li>
<li>Set a breakpoint in <code>app.ts</code></li>
</ul>

<blockquote>
  Update: TypeScript debugging is now added in 0.3.0
  
  Update: Always clear your breakpoints, then attach, then add breakpoints. This is a bug and has been reported.
</blockquote>

Enjoy debugging!
