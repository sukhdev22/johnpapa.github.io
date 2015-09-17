---
layout: post
title: Tip&#58; Getting Hierarchical Entities via ADO.NET Data Services from Silverlight
date: 2009-01-07 11:02
author: John
comments: true
categories: [Silverlight]
---
<p>ADO.NET Data Services (hereafter called Astoria) allows simple URI mapping to entity models. Pretty cool. We can also dive into the entity model and return hierarchical data. For example, a set of Customer entities can be returned without their children or the Customer can be returned with their children (their associated Orders entities). Here are some sample syntaxes for these …</p>  <p>So the following URI would get all of the customer entities</p>  <blockquote>   <p><a title="http://[yourdomain]/NorthwindDataService.svc/customers" href="http://[yourdomain]/NorthwindDataService.svc/customers">http://[yourdomain]/NorthwindDataService.svc/customers()</a></p> </blockquote>  <p>And the following URI gets you all the customers and all of their orders:</p>  <blockquote>   <p><a title="http://[yourdomain]/NorthwindDataService.svc/customers()?$expand=orders" href="http://[yourdomain]/NorthwindDataService.svc/customers()?$expand=orders">http://[yourdomain]/NorthwindDataService.svc/customers()?$expand=orders</a>&#160;</p> </blockquote>  <p>But what if you want to get grandchild entities? For example, getting the Customers, their orders, and the order details for those orders. The following URI does not work ….</p>  <blockquote>   <p><a title="http://[yourdomain]/NorthwindDataService.svc/customers(‘ALFKI’)?$expand=orders,orderdetails" href="http://[yourdomain]/NorthwindDataService.svc/customers(&lsquo;ALFKI&rsquo;)?$expand=orders,orderdetails">http://[yourdomain]/NorthwindDataService.svc/customers(‘ALFKI’)?$expand=orders,orderdetails</a> </p> </blockquote>  <p>That will yield an error of “Type 'NorthwindModel.Customer' does not have a property named 'OrderDetails'.” When the expand keyword sees a comma delimited list, it tries to associate that entityset with the one in the URI. In other words it looks for a property on the Customers entity for Orders and one for OrderDetails. OrderDetails does not exist on the Customers (its on the Orders) so it fails. </p>  <p>So how do you get hierarchical data like this? Here is an example that works. This gets the customer ALFKI, its orders, and its orders order details. This example shows the expand keyword has 2 parameters: Orders and Orders/OrderDetails. </p>  <blockquote>   <p><a title="http://[yourdomain]/NorthwindDataService.svc/Customers(&#39;ALFKI&#39;)?$expand=Orders,Orders/OrderDetails" href="http://[yourdomain]/NorthwindDataService.svc/Customers('ALFKI')?$expand=Orders,Orders/OrderDetails">http://[yourdomain]/NorthwindDataService.svc/Customers('ALFKI')?$expand=Orders,Orders/OrderDetails</a></p> </blockquote>  <p>Interestingly, a shortcut to the previous example that also works eliminates the first parameter (the Orders) but yields the same good results of a customer, his orders and his orders’ order details. When diving into a grandchild hierarchy like this, the Orders entities are implied. In other words, since we grab the customer and we are asking for its OrderDetails, it is implied that we want the orders that connect the customers to their order details.</p>  <blockquote>   <p><a title="http://[yourdomain]/NorthwindDataService.svc/Customers(&#39;ALFKI&#39;)?$expand=Orders/OrderDetails" href="http://[yourdomain]/NorthwindDataService.svc/Customers('ALFKI')?$expand=Orders/OrderDetails">http://[yourdomain]/NorthwindDataService.svc/Customers('ALFKI')?$expand=Orders/OrderDetails</a></p> </blockquote>  <p>So we can use the comma to ask for multiple entitysets hanging off an entityset or we can use the slash to dive into a hierarchy. In Silverlight we don’t need to use the URI, we can use LINQ to specify the queries (which then get translated to the URIs).</p>  <p>Both of the following LINQ queries will get the customers, their orders and their order details. </p>  <blockquote>   <pre class="csharpcode">var query =
from c <span class="kwrd">in</span> Context.Customers.Expand(<span class="str">&quot;Orders/OrderDetails&quot;</span>)
select c;</pre>
<p>OR</p>
<pre class="csharpcode">var query =
from c <span class="kwrd">in</span> Context.Customers.Expand(<span class="str">&quot;Orders&quot;</span>).Expand(<span class="str">&quot;Orders/OrderDetails&quot;</span>)
select c;</pre>
<style type="text/css">
.csharpcode, .csharpcode pre
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
.csharpcode .lnum { color: #606060; }</style></blockquote>
<p></p>
<p>So there you have it!</p>
<p><strong><font color="#ff0000">NOTE</font>: </strong>The more data you request, the larger the return set (obviously). Only request data you need. If you might need more data later, you can always ask for it using another URI call or possibly using the BeginLoadProperty from Silverlight. More on this in another post :)<style type="text/css">
.csharpcode, .csharpcode pre
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

