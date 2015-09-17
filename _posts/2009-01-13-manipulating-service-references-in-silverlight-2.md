---
layout: post
title: Manipulating Service References in Silverlight 2
date: 2009-01-13 09:52
author: John
comments: true
categories: [Silverlight]
---
<p>When developing a Silverlight 2 project that uses WCF service references or <strike>ADO.NET Data Services</strike> Astoria references, and you want to push the builds to a test server, there are a few changes that need to be made so the references point to the test server and not the dev box. </p>  <p><a href="http://wildermuth.com/2008/11/08/Controlling_Service_References_in_Silverlight_2">Shawn Wildermuth has a great post</a> on this topic that explains the problem and also explains that when dealing with WCF service references, the ServiceReference.ClientConfig file can either be simply edited or a better option is to use compilation symbols to make the changes at compile time. For example, Shawn points out that you can create 2 endpoints in code in the ServiceReference.ClientConfig file in the Silverlight project: 1 for dev box and 1 for the test server. Then, in code the service can be instantiated using the following code (from Shawn’s post):</p>  <pre class="csharpcode"><span class="preproc">#if</span> DEBUG
MyTestServiceClient svc = <span class="kwrd">new</span> MyTestServiceClient(<span class="str">&quot;TestEndpoint&quot;</span>);
<span class="preproc">#else</span>
MyTestServiceClient svc = <span class="kwrd">new</span> MyTestServiceClient(<span class="str">&quot;RealEndpoint&quot;</span>);
<span class="preproc">#endif</span></pre>
<p>This same technique can be adapted for Astoria by flipping the service reference’s context object’s instantiation as shown below:</p>
<pre class="csharpcode"><span class="preproc">#if</span> DEBUG
<span class="kwrd">protected</span> MyEntities Context
{
get
{
<span class="kwrd">if</span> (_context == <span class="kwrd">null</span>)
_context = <span class="kwrd">new</span> MyEntities(
<span class="kwrd">new</span> Uri(<span class="str">&quot;MyService.svc&quot;</span>, UriKind.Relative));
<span class="kwrd">return</span> _context;
}
}
<span class="preproc">#else</span>
<span class="kwrd">protected</span> MyEntities Context
{
get
{
<span class="kwrd">if</span> (_context == <span class="kwrd">null</span>)
_context = <span class="kwrd">new</span> MyEntities(
<span class="kwrd">new</span> Uri(<span class="str">&quot;http://testbox/foo/MyService.svc&quot;</span>,
UriKind. Absolute));
<span class="kwrd">return</span> _context;
}
<span class="preproc">#endif</span></pre>
<p>Now simply choose the compilation options for when building and you are all set! Quite simple and effective. </p>
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
.csharpcode .lnum { color: #606060; }</style>

