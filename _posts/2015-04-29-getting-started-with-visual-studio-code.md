---
layout: post
title: Getting Started with Visual Studio Code
date: 2015-04-29 18:30
author: John
comments: true
categories: [Uncategorized]
---
When playing with VSCode, it may be helpful to start with a project. Grab your own or use Hot Towel to generate. You can <a href="https://github.com/johnpapa/generator-hottowel#prerequisites">install Hot Towel and generate a project quickly using these instructions</a>.

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

<h2>Quick Access</h2>

I find myself looking for a file, a variable, a function, a git command, or a task quite often. Especially when I do not know exactly where it is. VSCode provides quick access to these through quick access palettes and commands.

<h3>Command Palette</h3>

<code>CMD+SHIFT+P</code> opens the command palette. You can type what you are looking for and perform that action easily. No need to remember menu items or where that button may be hiding. Want to change your theme? Configure debugging? Open keyboard mapping preferences? Run tasks? Open a new console/terminal? This is the place. It's also a great place to just scroll through the entire list of available commands.

<blockquote>
  The name "Palette" and the idea is inspired by Sublime Text, which made this an immensely popular and useful feature.
</blockquote>

<code>CMD+SHIFT+P</code> is the most helpful keystroke you'll use in Visual Studio Code.  It also shows the keyboard mapping for each command.

<img src="http://www.johnpapa.net/wp-content/uploads/2015/04/cmdp.png" alt="CMD+P" />

<blockquote>
  Notice that you can delete the <code>&gt;</code> and you are at the Navigate to File or Symbol palette. This is a nice feature so you can move between the various palettes easily.
</blockquote>

<h3>Navigate to File</h3>

<code>CMD+P</code> opens the generic command palette where you can search for any file or symbol in one place. You can also see recently opened files.

<strong>UPDATE: The 0.2.0 release on 05.29.2015 this was remapped from CMD+O to CMD+P</strong>

<img src="http://www.johnpapa.net/wp-content/uploads/2015/04/cmdo.png" alt="CMD+O" />

<h3>Palettes ?</h3>

Are you sensing a theme here? There are a few palettes to remember. But the good news here is that if you forget which command does what, you can always type <code>?</code> to see the various ways you can find and navigate to what you want. Type <code>CMD+P</code> and then <code>?</code> to see a list.

You can also access this by <code>CMD+SHIFT+P</code> then delete the <code>&gt;</code>.

<img src="http://www.johnpapa.net/wp-content/uploads/2015/04/palettes.png" alt="palettes" />

<h3>Go to Symbol</h3>

<code>CMD+SHIFT+O</code> opens the Go to Symbol palette. The <code>@</code> prefix tells VSCode that you are searching for a symbol. You can then search for a local variable or function.

<img src="http://www.johnpapa.net/wp-content/uploads/2015/04/gotosymbol1.png" alt="CMD+SHIFT+O" />

You can also access this by <code>CMD+SHIFT+P</code> then delete the <code>&gt;</code> and type <code>@</code>.

VSCode is context aware when showing the symbols. This means it makes it easy to search for contextually appropriate symbols in various types of files. When in TypeScript, JavaScript or C# you can navigate to symbols. When in CSS, LESS or SASS you can navigate to rules. When in JSON files, you can navigate to arrays or objects. When in special files such as <code>keybindings.json</code>, you can navigate to the assigned key bindings (due to the awareness of a JSON schema).

<h3>Go to Symbol by Category</h3>

<code>CMD+SHIFT+O</code> opens the Go to Symbol palette, and typing an additional <code>:</code> allows you to search by category.

This is context sensitive so in code it may categorize by property or function.

<img src="http://www.johnpapa.net/wp-content/uploads/2015/04/gotosymbol2.png" alt="symbol in code" />

While in json it may search by array, object or string.

<img src="http://www.johnpapa.net/wp-content/uploads/2015/04/gotosymbol3.png" alt="symbol in json" />

<h3>Open Symbol by Name</h3>

<code>CMD+P</code> and type <code>#</code> so find a symbol by its name.

This is context sensitive so in code it may categorize by property or function. For example, you can search for a symbol across your entire project. It searches the beginning of each symbol and it is clever enough to search by the changes in camel case (as shown below).

<img src="http://www.johnpapa.net/wp-content/uploads/2015/04/symbolsearch.png" alt="symbol by name" />

<h3>Show Errors or Warnings</h3>

<code>CMD+SHIFT+M</code> then type <code>!</code> shows all of the current warnings or errors in the Error palette. You can also open the Error palette by clicking on the error and warnings counter in the status bar.

<img src="http://www.johnpapa.net/wp-content/uploads/2015/04/warnings.png" alt="warnings" />

<h3>Help for Commands</h3>

<code>CMD+P</code> then type <code>?</code> shows all of the types of global and editor commands you can run.

<img src="http://www.johnpapa.net/wp-content/uploads/2015/04/question.png" alt="question" />

<blockquote>
  We'll take a look at the git and task commands later in this post.
</blockquote>

<h2>Editor</h2>

<h3>New Instances</h3>

I often want multiple instances of a tool open to work with different projects. VSCode makes this easy. Simply type <code>CMD+SHIFT+N</code> and a new instance of VSCode is opened.Here is show 2 instances (shrunken down a bit) with 2 different projects.

<img src="http://www.johnpapa.net/wp-content/uploads/2015/04/instances.png" alt="instances" />

<h3>New File</h3>

The simple <code>CMD+N</code> opens a new file. From here you can save, name it,  and keep on rolling.

<h3>Autosave</h3>

Tired of losing changes? Or are you like me where you hit <code>CMD+S</code> all day long? VSCode let's you enable automatic saving of files through a menu option. Me? I turned this on and never looked back.

<img src="http://www.johnpapa.net/wp-content/uploads/2015/04/autosave.png" alt="autosave" />

If you enable auto save and you have watchers on your files, those watchers will execute every time you change a file.

If you disable auto save and you make changes to a file, you will see dots next to the files in the Working Files list.

<img src="http://www.johnpapa.net/wp-content/uploads/2015/04/dirtyfiles.png" alt="dirtyfiles" />

<h3>Split the Editor</h3>

<code>CMD+\</code> will split the editor. This is great for opening and viewing multiple files side by side. Especially helpful for markdown and markdown preview. Even more helpful when transpiling LESS to CSS or TypeScript to JavaScript.

<img src="http://www.johnpapa.net/wp-content/uploads/2015/04/sidebyside.png" alt="sidebyside" />

You can also open the sidebar from <code>CMD+P</code> using the two rectangle icon. Or you can hold the <code>CMD</code> and click with the mouse on the file in the File Explorer to open it in a new side panel.

VSCode allows you to have up to 3 code panels open in the editor.

<h3>Toggle Sidebar</h3>

<code>CMD+B</code> will toggle the sidebar to be shown or hidden. This is great when you need more real estate on your screen.
