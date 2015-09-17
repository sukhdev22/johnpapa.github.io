---
layout: post
title: Better Demos with AutoHotKey
date: 2013-05-02 01:24
author: John
comments: true
categories: [course, pluralsight, presentation, speaking, Uncategorized]
---
Stressing over your upcoming presentation where you have to type a bunch of code from memory or from a script? <a href="http://www.autohotkey.com" target="_blank">AutoHotKey</a> can help you automate much of the "writing" of the code so you can write demos on the fly. AutoHotKey does so much more, but for a quick and simple way to write demos on the fly, it really is top-notch.

<blockquote>You can learn more about AutoHotKey and other presentation tips in my upcoming <a href="http://www.pluralsight.com" target="_blank">Pluralsight</a> course "<a href="http://jpapa.me/artspeaking" target="_blank">The Art of Public Speaking and Effective Presentations" <img src="http://www.johnpapa.net/wp-content/uploads/2013/05/artspeaking-600x91.png" alt="artspeaking" width="600" height="91" class="aligncenter size-large wp-image-17921" /></a>
</blockquote>

You could use notepad, a snippet tool, or even the toolbox in Visual Studio. But AutoHotKey provides more than those and it is a free tool. For example, AutoHotKey works in any editor. Create a script where you define your keystrokes and map them to code that will be pasted.

<h3>How it Helps</h3>
Lets say you are in a presentation and staring at a mostly blank code file. You are supposed to be typing in 30 lines of code from scratch. Instead of typing and making mistakes along the way, copying and pasting code, pulling in finished solutions, or using a toolbox, etc ... you can type the code in chunks. Point by point you fill in the blanks by typing custom keystroke mappings that you define.

Often I will start with a blank code file and then use bookmarks in Visual Studio to define where I want my code to go. Another technique I use is to start with an empty file that contains comments where the code should go. This way I know where each snippet should be entered.

<h3>Creating a Script</h3>
First, create a file with an <code>*.ahk</code> extension. Then edit that file in notepad, notepad++ or any other text editor. 

Next, create a keystroke mapping that when typed, and followed by a <code>TAB</code> keystroke, will paste your code snippet. The keystroke mapping should be surrounded by colons. Specifically, put 2 colons before the mapping and 2 colons after the mapping. Like this: <code> ::demo01:: </code>. Then when you type <code>demo01</code> followed by a <code>TAB</code> you should expect your code to be pasted.

Wait, what code? Right, it's time to show how to define the code that will be pasted. Following your keystroke mapping type <code>Clipboard = (   )</code>. This means when you type your keystroke mapping that it will copy whatever is inside the parenthesis to the clipboard of your PC. Easy enough. So this is where you put your code!

Put your code inside these parentheses, taking care to make sure you use the proper whitespace. Whatever you put in here is exactly what goes to the clipboard. 

Finally, now that you have told AutoHotKey what to move to the clipboard, you need to tell it to paste the code. You do that by sending the paste command using <code>send ^v</code> and wrapping up with the <code>return</code> keyword. 

The sample below puts this all together.

<pre class="prettyprint linenums">
::demo01::
Clipboard = 
(
        var saveChanges = function () {
            return manager.saveChanges()
                .then(saveSucceeded)
                .fail(saveFailed);
            

        };
)
send ^v
return
</pre>

Normally, I will have a few of these keystroke mappings in a ahk file. When you install AutoHotKey it adds a feature where you can right click a ahk file in windows explorer and then compile it. So you can compile the script by right clicking the file and choosing <code>compile script</code>. This creates an executable file, which of course you run.

Once the file is running, anytime you use the keystroke mappings followed by a <code>TAB</code> your code will be pasted (as long as you are in an editor of some sort).

This makes it really simple to create a script with a bunch of code snippets that you can type on the fly!

<h3>Try It Now</h3>
Try this out by downloading and installing AutoHotKey, compiling the script (scrape it from my post), running it, then typing the keystrokes in an editor.

