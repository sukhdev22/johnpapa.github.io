---
layout: post
title: FontAwesome Icons with Toastr
date: 2013-07-28 22:56
author: John
comments: true
categories: [css, fontawesome, javascript, toastr, Uncategorized]
---
What do you get when you combine <a href="http://fontawesome.io/" target="_blank">FontAwesome</a> icons with <a href="http://toastrjs.com" target="_blank">Toastr</a>? Maybe ToastrAwesome or ToastAwesomer. If you have used Toastr then you know you can use your own CSS styling and make the toast look however you desire. Toastr comes with 4 basic icons as background images, but what FontAwesome allows you to do is use its icons instead of a background image. This post will show you how to do that so you can use any of the FontAwesome icons with Toastr, using only CSS. 

<img src="http://www.johnpapa.net/wp-content/uploads/2013/07/toast.png" alt="toast" width="395" height="79" class="aligncenter size-full wp-image-19201" />

This technique uses the CSS psuedo-selectors and works in IE8+, FireFox 21+, Chrome 26+, Safari 5.1+, most mobile browsers, according to <a href="http://caniuse.com/#search=%3Abefore" target="_blank">CanIUse.com</a>. First, we need to remove the background-image and then we can set up our positioning for all toast content. You can tinker with the styles in the <code>.toastr:before</code> selector if you need something slightly different.

<pre class="prettyprint linenums">
#toast-container > .toast {
    background-image: none !important;
}

#toast-container > .toast:before {
    position: relative;
    font-family: FontAwesome;
    font-size: 24px;
    line-height: 18px;
    float: left;
    margin-left: -1em;
    color: #FFF;
    padding-right: 0.5em;
    margin-right: 0.5em;
}        
</pre>

Next we can tell toastr which icon to use for each of the 4 toast types. We set this through the CSS content and set it to the icon that you desire. Here is a <a href="http://fontawesome.io/cheatsheet/" target="_blank">cheatsheet from FontAwesome</a> that can help you pick the right one for you.

<pre class="prettyprint linenums">
#toast-container > .toast-warning:before {
    content: "\f003";
}
#toast-container > .toast-error:before {
    content: "\f001";
}
#toast-container > .toast-info:before {
    content: "\f005";
}
#toast-container > .toast-success:before {
    content: "\f002";
}
</pre>

And that's it! If you want to see a <a href="http://plnkr.co/edit/6W9URNyyp2ItO4aUWzBB?p=preview" target="_blank">full demo, check out this plunker I whipped up</a>.
