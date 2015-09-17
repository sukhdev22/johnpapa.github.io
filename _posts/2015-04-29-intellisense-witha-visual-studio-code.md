---
layout: post
title: Intellisense with Visual Studio Code
date: 2015-04-29 18:34
author: John
comments: true
categories: [Uncategorized]
---
Visual Studio Code provides excellent intellisense for JavaScript, TypeScript, and C#. Whether you are running ASP.NET 5 or node or client side code, you'll see a new level of intellisense here.

You can also hit <code>CTRL+SPACE</code> and get intellisense.

If you hover over a variable VSCode shows the signature of a function or the type of a variable, if it can be determined.

<img src="http://www.johnpapa.net/wp-content/uploads/2015/04/hover.png" alt="hover" />

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

<h2>JavaScript Intellisense</h2>

Out of the box we get basic intellisense for what the editor can determine on its own about the JavaScript code. VSCode will tell you a function's signature or what variables are available in scope.

<img src="http://www.johnpapa.net/wp-content/uploads/2015/04/js-hint1.png" alt="js-hint1" />

When working in node.js VSCode provides intellisense across all of your JavaScript modules (the ones you write).

<h3>Quick Fix</h3>

Now let's assume you want intellisense for the JavaScript libraries or node modules you use on the client or server. Perhaps you are using Angular and you want intellisense on it. Notice the green squiggly line under <code>angular</code>? Put your cursor on it then click the light bulb ( or <code>CMD+.</code> ) and choose <code>Add /// reference to angularjs/angular.d.ts</code>.

<img src="http://www.johnpapa.net/wp-content/uploads/2015/04/js-hint2.png" alt="js-hint2" />

VSCode will go and get the typings definition file for Angular and add it to your project, reference it in the file and you instantly have intellisense for Angular! (VSCode grabs the typings files from the Definately Typed repository.)

<img src="http://www.johnpapa.net/wp-content/uploads/2015/04/js-hint3.png" alt="js-hint3" />

We can now repeat this by adding jQuery code to a file. Put the cursor on the <code>$</code>, click <code>CMD+.</code>, and pull down the typings file. Now we have jQuery intellisense, too.

<h3>Consolidating into a tsd.d.ts</h3>

Do you see the 2 <code>///</code> references and how the can accumulate? You can make a single <code>tsd.d.ts</code> with the npm package named <code>tsd</code>.

<pre><code class="bash">npm install tsd -g
# cd to your project folder
tsd query -r -o -a install angular jquery
</code></pre>

This produces a <code>tsd.d.ts</code> file which you can reference in your JavaScript files to get intellisense. Now you have 1 place to put all of you typings for JavaScript projects.

<blockquote>
  I think the story for this will get even better too, since VSCode uses TypeScript under the covers for its tooling.
</blockquote>

<h3>Additional Hints</h3>

If you try to create a type in a JavaScript file, VSCode will warn you that it is not valid.

<img src="http://www.johnpapa.net/wp-content/uploads/2015/04/js-hint4.png" alt="js-hint4" />

<h2>TypeScript Intellisense</h2>

The intellisense and editor experience is top notch when using TypeScript. VSCode provides intellisense across multiple files because TypeScript understands the <code>import</code> statement.

VSCode provides intellisense for third party libraries, if you include the typings <code>*.d.ts</code> files. This works the same as it does with JavaScript files. You can use the <a href="#quick-fix">Quick Fix</a> feature to add a typing automatically.

<h2>JSON Intellisense</h2>

Intellisense works in well known JSON files too, including <code>package.json</code> and <code>bower.json</code>. It uses schema information and looks up values to find likely matches, where possible.

Here you can see it finding all npm packages that match <code>gulp</code>.

<img src="http://www.johnpapa.net/wp-content/uploads/2015/04/jsonintellisense1.png" alt="jsonintellisense1.png" />

Here you can see it finding the most appropriate versions and showing a message about what the versions mean.

<img src="http://www.johnpapa.net/wp-content/uploads/2015/04/jsonintellisense2.png" alt="jsonintellisense2.png" />
