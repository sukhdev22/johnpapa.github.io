---
layout: post
title: Easy Fix to a Common Angular Module Error
date: 2014-05-27 18:33
author: John
comments: true
categories: [angular, Uncategorized]
---
<p>I love running my code right after making some new changes, so I can see them light up in the browser. But I don't love when error messages are not straight forward. At least not to me.</p>

<p>Recently I ran a project and was told ngLocale is not available! What? I'm not loading ngLocale, what does Angular want from me? After some digging in the console and Chrome debugger I uncovered more information about the issue.</p>

<pre><code>"[$injector:nomod] Module 'ngLocale' is not available! 
You either misspelled the module name or forgot to load it. 
If registering a module ensure that you specify the dependencies 
 as the second argument.
http://errors.angularjs.org/1.2.16/$injector/nomod?p0=ngLocale"    
</code></pre>

<p>This didn't help much but luckily I'd seen this before and recalled that it happens when I tried to include a module dependency that did not exist. This happens due to a number of reasons such as removing a script for index.html for a module but leaving in the module dependency or even misspelling a module dependency. (Turns out my issue was the former.) So this was easy to fix once you knew that.</p>

<p>But the message is not very clear. Or is it? I read the message to say that ngLocale is misspelled or not loaded. I wasn't using ngLocale so this threw me off at first. But after reading the message again it might be trying to tell me that a module (any module) was not spelled correctly or was not loaded. Ah! If that is the intent, then we can start looking at other module dependencies to resolve it.</p>

<p>Either way, I think this error message needs some refactoring. Hopefully this post helps you avoid or prevent this issue from being a time sink.</p>

