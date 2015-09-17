---
layout: post
title: Return a List<T> or a ObservableCollection<T>
date: 2008-07-22 14:57
author: John
comments: true
categories: [All]
---
<p>It's crazy generic method time! Here is a method I created for fun that either returns a List&lt;T&gt; or a ObservableCollection&lt;T&gt;, depending on what you pass in via generic parameters. It creates a list of Product entity instances with some fake data.</p> <p>The L stands for the type of ICollection you want to create and return. For example a List&lt;T&gt; or a ObservableColleciton&lt;T&gt;. The P stands for a Product class type. This could be replaced with any type of entity, just replace the condition of where : Product with the entity type of your choice.</p> <p>You can call it using this code:</p> <div class="csharpcode"><pre class="alt">List&lt;Product&gt;  productList = CreateProductList&lt;List&lt;Product&gt;, Product&gt;();</pre></div>
<div class="csharpcode">&nbsp;</div>
<div class="csharpcode">or</div>
<div class="csharpcode">&nbsp;</div>
<div class="csharpcode"><pre class="alt"><p>ObservableCollection&lt;Product&gt; productOC = </p><blockquote><p>           CreateProductList&lt;ObservableCollection&lt;Product&gt;, Product&gt;();</p></blockquote></pre></div>
<style type="text/css">.csharpcode, .csharpcode pre
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
.csharpcode .lnum { color: #606060; }
</style>
<div class="csharpcode">&nbsp;</div>
<style type="text/css">.csharpcode, .csharpcode pre
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
.csharpcode .lnum { color: #606060; }
</style>
<p>Its just for fun ... so enjoy.</p>
<div class="csharpcode"><pre class="alt"><span class="lnum">   1:  </span><span class="kwrd">private</span> L CreateProductList&lt;L, P&gt;()</pre><pre><span class="lnum">   2:  </span>    <span class="kwrd">where</span> P : Product, <span class="kwrd">new</span>()</pre><pre class="alt"><span class="lnum">   3:  </span>    <span class="kwrd">where</span> L : ICollection&lt;P&gt;, <span class="kwrd">new</span>()</pre><pre><span class="lnum">   4:  </span>{</pre><pre class="alt"><span class="lnum">   5:  </span>    L products = <span class="kwrd">new</span> L</pre><pre><span class="lnum">   6:  </span>{</pre><pre class="alt"><span class="lnum">   7:  </span>    <span class="kwrd">new</span> P</pre><pre><span class="lnum">   8:  </span>        {</pre><pre class="alt"><span class="lnum">   9:  </span>            ProductId = 70,</pre><pre><span class="lnum">  10:  </span>            ProductName = <span class="str">"Outback Lager"</span>,</pre><pre class="alt"><span class="lnum">  11:  </span>            QuantityPerUnit = <span class="str">"24 - 355 ml bottles"</span>,</pre><pre><span class="lnum">  12:  </span>            UnitsInStock = 15,</pre><pre class="alt"><span class="lnum">  13:  </span>            UnitPrice = 15,</pre><pre><span class="lnum">  14:  </span>            UnitsOnOrder = 10,</pre><pre class="alt"><span class="lnum">  15:  </span>            ReorderLevel = 30,</pre><pre><span class="lnum">  16:  </span>            Discontinued = <span class="kwrd">false</span></pre><pre class="alt"><span class="lnum">  17:  </span>        },</pre><pre><span class="lnum">  18:  </span>    <span class="kwrd">new</span> P</pre><pre class="alt"><span class="lnum">  19:  </span>        {</pre><pre><span class="lnum">  20:  </span>            ProductId = 71,</pre><pre class="alt"><span class="lnum">  21:  </span>            ProductName = <span class="str">"Flotemysost"</span>,</pre><pre><span class="lnum">  22:  </span>            QuantityPerUnit = <span class="str">"10 - 500 g pkgs."</span>,</pre><pre class="alt"><span class="lnum">  23:  </span>            UnitsInStock = 25,</pre><pre><span class="lnum">  24:  </span>            UnitPrice = (<span class="kwrd">decimal</span>)21.5,</pre><pre class="alt"><span class="lnum">  25:  </span>            UnitsOnOrder = 0,</pre><pre><span class="lnum">  26:  </span>            ReorderLevel = 0,</pre><pre class="alt"><span class="lnum">  27:  </span>            Discontinued = <span class="kwrd">false</span></pre><pre><span class="lnum">  28:  </span>        },</pre><pre class="alt"><span class="lnum">  29:  </span>    <span class="kwrd">new</span> P</pre><pre><span class="lnum">  30:  </span>        {</pre><pre class="alt"><span class="lnum">  31:  </span>            ProductId = 35,</pre><pre><span class="lnum">  32:  </span>            ProductName = <span class="str">"Steeleye Stout"</span>,</pre><pre class="alt"><span class="lnum">  33:  </span>            QuantityPerUnit = <span class="str">"24 - 12 oz bottles"</span>,</pre><pre><span class="lnum">  34:  </span>            UnitsInStock = 20,</pre><pre class="alt"><span class="lnum">  35:  </span>            UnitPrice = (<span class="kwrd">decimal</span>)18,</pre><pre><span class="lnum">  36:  </span>            UnitsOnOrder = 0,</pre><pre class="alt"><span class="lnum">  37:  </span>            ReorderLevel = 15,</pre><pre><span class="lnum">  38:  </span>            Discontinued = <span class="kwrd">false</span></pre><pre class="alt"><span class="lnum">  39:  </span>        },</pre><pre><span class="lnum">  40:  </span>    <span class="kwrd">new</span> P</pre><pre class="alt"><span class="lnum">  41:  </span>        {</pre><pre><span class="lnum">  42:  </span>            ProductId = 53,</pre><pre class="alt"><span class="lnum">  43:  </span>            ProductName = <span class="str">"Perth Pasties"</span>,</pre><pre><span class="lnum">  44:  </span>            QuantityPerUnit = <span class="str">"48 pieces"</span>,</pre><pre class="alt"><span class="lnum">  45:  </span>            UnitsInStock = 0,</pre><pre><span class="lnum">  46:  </span>            UnitPrice = (<span class="kwrd">decimal</span>)32.80,</pre><pre class="alt"><span class="lnum">  47:  </span>            UnitsOnOrder = 0,</pre><pre><span class="lnum">  48:  </span>            ReorderLevel = 0,</pre><pre class="alt"><span class="lnum">  49:  </span>            Discontinued = <span class="kwrd">true</span>,</pre><pre><span class="lnum">  50:  </span>            DiscontinuedDate = <span class="kwrd">new</span> DateTime(1996, 7, 4)</pre><pre class="alt"><span class="lnum">  51:  </span>        }</pre><pre><span class="lnum">  52:  </span>};</pre><pre class="alt"><span class="lnum">  53:  </span>    <span class="kwrd">return</span> products;</pre><pre><span class="lnum">  54:  </span>}</pre></div>
<style type="text/css">.csharpcode, .csharpcode pre
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
.csharpcode .lnum { color: #606060; }
</style>

