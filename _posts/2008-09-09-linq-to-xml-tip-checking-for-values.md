---
layout: post
title: LINQ to XML Tip - Checking for Values
date: 2008-09-09 14:44
author: John
comments: true
categories: [Silverlight]
---
<p>This tip comes right from some of the examples I am writing for my book Data Services with Silverlight 2. I was writing a LINQ query definition&nbsp; for LINQ to XML that parses through a response from an Amazon RESTful web service when I realized I cannot be sure if a book will have a price stored in this XML element, or that element, or some other element. So I had to check to see what element existed and contained the appropriate value.</p>
<p>So I ran a query like this:</p>
<div class="csharpcode">
<pre class="alt">
var bookQuery = </pre>
<pre>
from book <span class="kwrd">in</span> bookXml.Descendants(<span class="str">&quot;Item&quot;</span>)</pre>
<pre class="alt">
&nbsp;</pre>
<pre>
let attributes = book.Element(<span class="str">&quot;ItemAttributes&quot;</span>)</pre>
<pre class="alt">
&nbsp;</pre>
<pre>
let price = Decimal.Parse((</pre>
<pre class="alt">
book.Elements(<span class="str">&quot;OfferSummary&quot;</span>).Any() </pre>
<pre>
&amp;&amp; book.Element(<span class="str">&quot;OfferSummary&quot;</span>).Elements(<span class="str">&quot;LowestNewPrice&quot;</span>).Any()</pre>
<pre class="alt">
? book.Element(<span class="str">&quot;OfferSummary&quot;</span>).Element(<span class="str">&quot;LowestNewPrice&quot;</span>).Element(<span class="str">&quot;Amount&quot;</span>).Value</pre>
<pre>
: (attributes.Elements(<span class="str">&quot;ListPrice&quot;</span>).Any()</pre>
<pre class="alt">
? attributes.Element(<span class="str">&quot;ListPrice&quot;</span>).Element(<span class="str">&quot;Amount&quot;</span>).Value </pre>
<pre>
: <span class="str">&quot;0&quot;</span>))) / 100</pre>
<pre class="alt">
&nbsp;</pre>
<pre>
select <span class="kwrd">new</span> {Price = price};</pre>
</div>
<p><style type="text/css">.csharpcode, .csharpcode pre
{
font-size: small;
color: black;
font-family: consolas, "Courier New", courier, monospace;
background-color: #ffffff;
/*white-space: pre;*/
}
.csharpcode pre { margin: 0em; }
.csharpcode .rem { color: #008000; }
.csharpcode .kwrd { color: #0000ff; }
.csharpcode .str { color: #006080; }
.csharpcode .op { color: #0000c0; }
.csharpcode .preproc { color: #cc6633; }
.csharpcode .asp { background-color: #ffff00; }
.csharpcode .html { color: #800000; }
.csharpcode .attr { color: #ff0000; }
.csharpcode .alt
{
background-color: #f4f4f4;
width: 100%;
margin: 0em;
}
.csharpcode .lnum { color: #606060; }</style><style type="text/css">.csharpcode, .csharpcode pre
{
font-size: small;
color: black;
font-family: consolas, "Courier New", courier, monospace;
background-color: #ffffff;
/*white-space: pre;*/
}
.csharpcode pre { margin: 0em; }
.csharpcode .rem { color: #008000; }
.csharpcode .kwrd { color: #0000ff; }
.csharpcode .str { color: #006080; }
.csharpcode .op { color: #0000c0; }
.csharpcode .preproc { color: #cc6633; }
.csharpcode .asp { background-color: #ffff00; }
.csharpcode .html { color: #800000; }
.csharpcode .attr { color: #ff0000; }
.csharpcode .alt
{
background-color: #f4f4f4;
width: 100%;
margin: 0em;
}
.csharpcode .lnum { color: #606060; }</style></p>
<p>The problem was that the price could be stored in the OfferSummary element if an offer exists for the item (a book in my case). But the OfferSummary element ay not even exist. If it does, then I have to check for the LowestNewPrice element and it may not exist. Finally if it does, I go ge the Amount element and grab its value. Otherwise I have to get get the ListPrice element. But it may not exist either. I think you get the point ... sometimes the elements exist and sometimes they don't.</p>
<p>So one way around this is to check if the element exists by using the Elements collection (instead of the Element ... singular) and using its Any() method. This returns a boolean value that tells if any items exist in that collection. So the above code makes sure I get a price whether it be the lower offer price or the current list price (as a fallback). If no price exists, it returns a 0. All of this is done outside of the select statement in the LINQ query definition. This allows the select to remain unclutterred. As you can see, the let statement for the price got ugly quick.</p>
<p>Using the Elements(&quot;foo&quot;).Any() technique is pretty easy to do and makes it easier to grab a value and prep.</p>

