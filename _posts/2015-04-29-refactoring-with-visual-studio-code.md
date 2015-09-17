---
layout: post
title: Refactoring with Visual Studio Code
date: 2015-04-29 18:34
author: John
comments: true
categories: [Uncategorized]
---
Visual Studio Code has some awesome refactoring features. Here are some of my favorites.

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

<h2>Move Line Up / Down</h2>

VSCode will move a line up when you use <code>OPT+UPARROW</code> or down when you use <code>OPT+DOWNARROW</code>.

<h2>Go to Next Error or Warning</h2>

When you have multiple errors or warnings, you can visit each of them in the current file using the Go to Next Error or Warning. Press <code>F8</code> and you will see the first error or warning. Press <code>F8</code> again and you will see the next one.

<img src="http://www.johnpapa.net/wp-content/uploads/2015/04/goto-marker.png" alt="go to marker" />

<h2>Go to Definition</h2>

When you are looking at your code and you want to find where a function or variable is defined, you can press <code>F12</code> to navigate to the definition. This works in the same file or to another file when using TypeScript.

<h2>Peek at Definition</h2>

This is like the <a href="go-to-definition">Go to Definition</a> except instead of navigating to the definition a window appears showing you a peek of the definition. Seeing is believing, so check this out below, using <code>OPTION F12</code>

<img src="http://www.johnpapa.net/wp-content/uploads/2015/04/peek1.png" alt="peek1" />

You can edit either file in this mode. If you want to navigate to the file, click on the file name in the header of the peek view. You can exit this mode and close the peek by clicking <code>ESC</code>.

<h2>Find All References</h2>

VSCode help you find all references of a variable, everywhere it can be determined that it is being used, with <code>SHIFT F12</code>. This works incredibly well with TypeScript. VSCode uses TypeScript to figure out how to find those references. As such, this feature works less great in JavaScript.

This is helpful when refactoring so you can find all of the places a function or property may be used before refactoring.

Notice that the files are displayed to the right. You can click on these to see each references.

<img src="http://www.johnpapa.net/wp-content/uploads/2015/04/far.png" alt="far" />

<h2>Change All Occurrences</h2>

Put your cursor in a variable or function and click <code>CMD+F2</code> then begin typing. This will find all occurrences in the open file and change them as you type, which is ideal for local refactoring.

<img src="http://www.johnpapa.net/wp-content/uploads/2015/04/change-occurences.png" alt="change-occurrences.png" />

<h2>Multi-Cursor</h2>

Click + <code>OPTION</code> in your code. Then find another place in code and repeat, and repeat, and repeat. Now you have multiple cursors in the file and you can edit all of them at once!

<img src="http://www.johnpapa.net/wp-content/uploads/2015/04/multicursor1.png" alt="multicursor1" />

I love this, but I really want to also be able to do this through search via keyboard so I can find all instances of a phrase and then edit.

<h2>Rename symbols in all files ( <code>F2</code> )</h2>

Sometimes you want to rename in 1 file, and other times you want to rename across multiple files. For example, you may want to rename a publicly accessible function on an Angular service and have everywhere that uses it get updated.

First put your cursor on the member and click <code>F2</code>.

<img src="http://www.johnpapa.net/wp-content/uploads/2015/04/rename1.png" alt="rename1.png" />

Then type the new name and hit the <code>Enter</code> key. This will rename all of the occurrences in every file in your project.

This shows the newly renamed <code>getThePeople</code> method in the <code>dataservice.ts</code> file.
<img src="http://www.johnpapa.net/wp-content/uploads/2015/04/rename2.png" alt="rename2.png" />

This shows the newly renamed <code>getThePeople</code> method in the <code>dashboard.controller.ts</code> file.
<img src="http://www.johnpapa.net/wp-content/uploads/2015/04/rename3.png" alt="rename3.png" />

<h2>Format Code</h2>

VSCode makes it easy to format your code with the appropriate indentation and alignment through it's Format Code command. Just select the code block you want to format, use <code>CMD+SHIFT+P</code> to open the command palette, and type <code>format code</code>. You can also type part of the command as it will do partial matching.
