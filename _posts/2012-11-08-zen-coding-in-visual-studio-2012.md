---
layout: post
title: Zen Coding in Visual Studio 2012
date: 2012-11-08 20:58
author: John
comments: true
categories: [html, html5, Uncategorized, visual studio 2012, web essentials, zen coding]
---
<div>Zen Coding is a faster way to write HTML using a CSS style selector syntax, and you can now use Zen Coding in Visual Studio via the <a href="http://jpapa.me/webess2012" target="_blank">Web Essentials 2012 plug in</a> (v1.7).  <a href="http://code.google.com/p/zen-coding/" target="_blank">Zen Coding</a> was introduced by Sergey Chikuyonok in 2009 (according to Smashing Magazine) and has been updated over time to become a great way to write monotonous HTML much more efficiently.</div>
<div></div>
<blockquote>
<div>Special thanks  to <a href="https://twitter.com/mkristensen" target="_blank">Mads Kristensen</a> and his team at Microsoft for adding Zen Coding to Visual Studio 2012 via Web Essentials 2012 (along with many other great features).</div></blockquote>
<h2>Quick Reference</h2>
Here is a quick list of the Zen Coding features that are now supported in Visual Studio 2012 via the <a href="http://jpapa.me/webess2012" target="_blank">Web Essentials 2012 plug in</a>
<ul>
	<li><strong>#</strong> creates an id attribute</li>
	<li><strong>.</strong> creates a class attribute</li>
	<li><strong>[ ]</strong> creates a custom attribute</li>
	<li><strong>&gt;</strong> creates a child element</li>
	<li><strong>+</strong> creates a sibling element</li>
	<li><strong>^</strong> climbs up</li>
	<li><strong>*</strong> is element multiplication. This creates the same thing n number of times</li>
	<li><strong>$</strong> is replaced with an incremental number</li>
	<li><strong>$$</strong> is used for numbers with padding</li>
	<li><strong>{ }</strong> creates text in an element</li>
</ul>
<div>What can you do? Here is an example:</div>
<pre class="prettyprint linenums"><!-- Type this -->
ul[data-bind="foreach:customers"]>li*4>span{Caption $$}+input[type=text data-bind="value:$$"]

<!-- Creates this -->
<ul data-bind="foreach:customers">
    <li><span>Caption 01</span><input type="text" value="" data-bind="value:01" /></li>
    <li><span>Caption 02</span><input type="text" value="" data-bind="value:02" /></li>
    <li><span>Caption 03</span><input type="text" value="" data-bind="value:03" /></li>
    <li><span>Caption 04</span><input type="text" value="" data-bind="value:04" /></li>
</ul>
</pre>
<div>Let's take a closer look at the different symbols used</div>
<h2>ID and Class Attributes: # and .</h2>
<div>You can create an element and assign it an id or class attribute using CSS style syntax.</div>
<pre class="prettyprint linenums"><!-- Type this -->
div#contentRegion.address

<!-- Creates this -->
<div id="contentRegion" class="address"></div>
</pre>
<h2>Custom Attributes: [ ]</h2>
<div>You can create any attribute the square bracket syntax.</div>
<pre class="prettyprint linenums"><!-- Type this -->
div[title]

<!-- Creates this -->
<div title=""></div>
</pre>
<div>Or create multiple attributes and fill in values</div>
<pre class="prettyprint linenums"><!-- Type this -->
input[placeholder="Name" type="text"]

<!-- Creates this -->
<input type="text" value="" placeholder="Name" />
</pre>
<h2>Child Elements: &gt;</h2>
<div>Create an element and then a child element inside of it. In this example I create a div with the id=menu that contains a span with a class=item and a blank title attribute</div>
<pre class="prettyprint linenums"><!-- Type this -->
div#menu>span.item[title]

<!-- Creates this -->
<div id="menu">
    <span class="item" title=""></span>
</div>
</pre>
<h2>Sibling Elements: +</h2>
<div>You can create a sibling element easily too.</div>
<pre class="prettyprint linenums"><!-- Type this -->
footer>div>a+input

<!-- Creates this -->
<footer>
    <div>
        <a href=""></a>
        <input type value="" />
    </div>
</footer>
</pre>
<h2>Climbing Elements: ^</h2>
<div>The &gt; operator descends into element hierarchy while the ^ climbs up the hierarchy. You can also climb multiple levels. For example: use 1 ^ to climb 1 level or use 4 ^ to climb 4 levels.</div>
<pre class="prettyprint linenums"><!-- Type this -->
footer>div>a+input^^p

<!-- Creates this -->
<footer>
    <div>
        <a href=""></a>
        <input type value="" />
    </div>
    <p></p>
</footer>
</pre>
<h2>Multiplication: *</h2>
<div>Create n number of elements</div>
<pre class="prettyprint linenums"><!-- Type this -->
ul>li*4>span

<!-- Creates this -->
<ul>
    <li><span></span></li>
    <li><span></span></li>
    <li><span></span></li>
    <li><span></span></li>
</ul>
</pre>
<h2>Item Numbering: $</h2>
<div>When using the multiplication to create n number of elements, you can add an incremental number to them using the $. Notice that using multiple $ operators (ex: $$) creates pads the numbers with 0's.</div>
<pre class="prettyprint linenums"><!-- Type this -->
section>article.item$$*4

<!-- Creates this -->
<section>
    <article class="item01"></article>
    <article class="item02"></article>
    <article class="item03"></article>
    <article class="item04"></article>
</section>
</pre>
<h2>Text: } {</h2>
<div>You can enter text values inside of elements, without changing the parent context.</div>
<pre class="prettyprint linenums"><!-- Type this -->
ul>li*4>span{Caption $$}

<!-- Creates this -->
<ul>
    <li><span>Caption 01</span></li>
    <li><span>Caption 02</span></li>
    <li><span>Caption 03</span></li>
    <li><span>Caption 04</span></li>
</ul>
</pre>
<div>This does not change the parent context, so when specifying the sibling to follow the text, the sibling element will actually follow the element prior to the text. That's why the example below creates an anchor tag next to the span tag.</div>
<pre class="prettyprint linenums"><!-- Type this -->
ul>li*4>span{Caption $$}+a{click me}

<!-- Creates this -->
<ul>
    <li><span>Caption 01</span><a href="">click me</a></li>
    <li><span>Caption 02</span><a href="">click me</a></li>
    <li><span>Caption 03</span><a href="">click me</a></li>
    <li><span>Caption 04</span><a href="">click me</a></li>
</ul>
</pre>
<h2>Combining Them all</h2>
<div>You can combine multiple features together which allows you to write some pretty cool HTML much faster. You can even use this to create some <a href="http://www.knockout.js.com" target="_blank">Knockout.js</a> bindings for templates, and then just change the property names.</div>
<pre class="prettyprint linenums"><!-- Type this -->
section[data-bind="foreach:customers"]>div*4>input[type="text" data-bind="text:$$"]

<!-- Creates this -->

<section data-bind="foreach:customers">
    <div>
        <input type="text" value="" data-bind="text:01" />
    </div>
    <div>
        <input type="text" value="" data-bind="text:02" />
    </div>
    <div>
        <input type="text" value="" data-bind="text:03" />
    </div>
    <div>
        <input type="text" value="" data-bind="text:04" />
    </div>
</section>
</pre>
<h2>Grouping: ( )</h2>
<div>Grouping is a powerful feature of Zen Coding that allows you to create complex expressions. It is not yet in Web Essentials 2012, but I assume it will come in the near future. If it does arrive, you would be able to create entire sections of a DOM very easily.</div>
<pre class="prettyprint linenums"><!-- Type this -->
div>(header>div)+section>(ul>li*2>a)+footer>(div>span)

<!-- WOULD create this (not yet supported in Web Essentials 2012)-->
<div>
    <header>
        <div></div>
    </header>
    <section>
        <ul>
            <li><a href=""></a></li>
            <li><a href=""></a></li>
        </ul>
    </section>
    <footer>
        <div>
            <span></span>
        </div>
    </footer>
</div>
</pre>

<div>As you can see, this would make it quite simple to create large sections of HTML with just a few keystrokes.</div>


<h2>Lorem Ipsum Generator</h2>
<div>
<em>(Added Dec 5, 2012)</em>

You can now generate Lorem Ipsum directly in the HTML editor. Type "lorem" and hit TAB and a 30 word Lorem Ipsum text is inserted. Type "lorem10" and a 10 word Lorem Ipsum text is inserted.
</div>

<pre class="prettyprint">
ul>li*5>lorem3
</pre>

<h2>References</h2>
<div>
<ul>
	<li><a href="http://code.google.com/p/zen-coding/" target="_blank">Zen Coding page</a></li>
	<li>Follow <a href="http://twitter.com/zen_coding" target="_blank">Zen C0ding</a> on twitter</li>
	<li><a href="http://coding.smashingmagazine.com/2009/11/21/zen-coding-a-new-way-to-write-html-code/" target="_blank">Introduction to  Zen Coding from Smashing Magazine in Nov 2009</a></li>
	<li><a href="http://jpapa.me/webess2012" target="_blank">Web Essentials 2012</a> for Visual Studio 2012</li>
</ul>
</div>



