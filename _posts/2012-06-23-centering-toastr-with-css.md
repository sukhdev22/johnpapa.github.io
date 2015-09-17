---
layout: post
title: Centering toastr with CSS and Media Queries
date: 2012-06-23 15:11
author: John
comments: true
categories: [css, media queries, toastr, Uncategorized]
---
<a href="https://github.com/CodeSeven/toastr">Toastr was released almost 2 months</a> ago and has had a nice response so far. We’ve kept it simple yet extendable and we’ve received a lot of good feedback over it. One interesting point we never explored was how customizable toastr already. Much of its appearance and behavior can be customized through CSS or JavaScript. For example, Hans and I provided 4 standard positions for the toastr messages in the 4 corners of the page, but you can change that too.

<a href="/toastr100beta#comment-3844">Over in my original toastr post a reader asked a question</a> about if it is possible to center toastr’s messages at the top center. The answer is yes, and in fact you can position toastr however you like. The keys are to create some CSS to style the toast container and then set the toastr.options.positionClass property.

All toastr messages appear in a container div, which means all toasts will stack up inside of it. Out of the box toastr offers 4 positioning settings with CSS class names. These are set to the toastr.options.positionClass property.

Here is some possible CSS to style the toast at the top center
<pre class="prettyprint linenums">.toast-top-center { 
    top: 12px; 
    left: 50%; 
    margin-left: -150px; 
} 
@media all and (max-width: 240px) { 
    .toast-top-center { 
        margin-left: -54px; 
    } 
} 
@media all and (min-width: 241px) and (max-width: 320px) { 
    .toast-top-center { 
        margin-left: -64px; 
    } 
} 
@media all and (min-width: 321px) and (max-width: 480px) { 
    .toast-top-center { 
        margin-left: -96px; 
    } 
}</pre>
&nbsp;

Notice that I set the media queries to adjust the position, too. I used the width of the toast to adjust the centering (the width is 300px by default). But when the screen changes there are media queries in the toastr-responsive.css file that adjust toastr’s width for smaller devices sizes. So I need these media queries to adjust the margin-left positions too. Of course, you can use any technique you like to position with CSS.

Then set the positionClass property like this (the name is totally up to you, as long as it matches the name of the CSS class you created):
<pre class="prettyprint">toastr.options.positionClass = 'toast-top-center'</pre>
This is just one way you can customize toastr.
