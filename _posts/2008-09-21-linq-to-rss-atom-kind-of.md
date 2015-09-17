---
layout: post
title: LINQ to RSS/ATOM (Kind of)
date: 2008-09-21 02:02
author: John
comments: true
categories: [Silverlight]
---
<p>While working through some examples for my book that use the SyndicationFeed and SyndicationItem classes to manage RSS and ATOM data, I wrote this little LINQ to Objects query that mashes items from several different feeds together, and sorts them by date. Its pretty basic LINQ, but when combined with the way cool SyndicationFeed and SyndicationItem classes, I think its pretty darn awesome. :) I&rsquo;m just thrilled we have these types of tools at our disposal, instead of writing RSS/ATOM parsing routines from scratch using the XmlReader. I&rsquo;ve done that waaaaaaay too often &hellip; but not anymore.</p>
<p><strong>C#</strong></p>
<div>
<div style="padding-right: 0px; padding-left: 0px; font-size: 8pt; padding-bottom: 0px; overflow: visible; width: 100%; color: black; border-top-style: none; line-height: 12pt; padding-top: 0px; font-family: consolas, 'Courier New', courier, monospace; border-right-style: none; border-left-style: none; background-color: #f4f4f4; border-bottom-style: none">
<pre style="padding-right: 0px; padding-left: 0px; font-size: 8pt; padding-bottom: 0px; margin: 0em; overflow: visible; width: 100%; color: black; border-top-style: none; line-height: 12pt; padding-top: 0px; font-family: consolas, 'Courier New', courier, monospace; border-right-style: none; border-left-style: none; background-color: white; border-bottom-style: none">
var query = from f <span style="color: #0000ff">in</span> _feeds</pre>
<pre style="padding-right: 0px; padding-left: 0px; font-size: 8pt; padding-bottom: 0px; margin: 0em; overflow: visible; width: 100%; color: black; border-top-style: none; line-height: 12pt; padding-top: 0px; font-family: consolas, 'Courier New', courier, monospace; border-right-style: none; border-left-style: none; background-color: #f4f4f4; border-bottom-style: none">
from i <span style="color: #0000ff">in</span> f.Items</pre>
<pre style="padding-right: 0px; padding-left: 0px; font-size: 8pt; padding-bottom: 0px; margin: 0em; overflow: visible; width: 100%; color: black; border-top-style: none; line-height: 12pt; padding-top: 0px; font-family: consolas, 'Courier New', courier, monospace; border-right-style: none; border-left-style: none; background-color: white; border-bottom-style: none">
orderby i.PublishDate descending</pre>
<pre style="padding-right: 0px; padding-left: 0px; font-size: 8pt; padding-bottom: 0px; margin: 0em; overflow: visible; width: 100%; color: black; border-top-style: none; line-height: 12pt; padding-top: 0px; font-family: consolas, 'Courier New', courier, monospace; border-right-style: none; border-left-style: none; background-color: #f4f4f4; border-bottom-style: none">
select i;</pre>
</div>
</div>
<p><strong>VB</strong></p>
<div>
<div style="padding-right: 0px; padding-left: 0px; font-size: 8pt; padding-bottom: 0px; overflow: visible; width: 100%; color: black; border-top-style: none; line-height: 12pt; padding-top: 0px; font-family: consolas, 'Courier New', courier, monospace; border-right-style: none; border-left-style: none; background-color: #f4f4f4; border-bottom-style: none">
<pre style="padding-right: 0px; padding-left: 0px; font-size: 8pt; padding-bottom: 0px; margin: 0em; overflow: visible; width: 100%; color: black; border-top-style: none; line-height: 12pt; padding-top: 0px; font-family: consolas, 'Courier New', courier, monospace; border-right-style: none; border-left-style: none; background-color: white; border-bottom-style: none"><span style="color: #0000ff">Dim</span> query = _</pre>
<pre style="padding-right: 0px; padding-left: 0px; font-size: 8pt; padding-bottom: 0px; margin: 0em; overflow: visible; width: 100%; color: black; border-top-style: none; line-height: 12pt; padding-top: 0px; font-family: consolas, 'Courier New', courier, monospace; border-right-style: none; border-left-style: none; background-color: #f4f4f4; border-bottom-style: none">
From f <span style="color: #0000ff">In</span> _feeds , i <span style="color: #0000ff">In</span> f.Items _</pre>
<pre style="padding-right: 0px; padding-left: 0px; font-size: 8pt; padding-bottom: 0px; margin: 0em; overflow: visible; width: 100%; color: black; border-top-style: none; line-height: 12pt; padding-top: 0px; font-family: consolas, 'Courier New', courier, monospace; border-right-style: none; border-left-style: none; background-color: white; border-bottom-style: none">
Order By i.PublishDate Descending _</pre>
<pre style="padding-right: 0px; padding-left: 0px; font-size: 8pt; padding-bottom: 0px; margin: 0em; overflow: visible; width: 100%; color: black; border-top-style: none; line-height: 12pt; padding-top: 0px; font-family: consolas, 'Courier New', courier, monospace; border-right-style: none; border-left-style: none; background-color: #f4f4f4; border-bottom-style: none">
<span style="color: #0000ff">Select</span> i</pre>
<pre style="padding-right: 0px; padding-left: 0px; font-size: 8pt; padding-bottom: 0px; margin: 0em; overflow: visible; width: 100%; color: black; border-top-style: none; line-height: 12pt; padding-top: 0px; font-family: consolas, 'Courier New', courier, monospace; border-right-style: none; border-left-style: none; background-color: white; border-bottom-style: none">&nbsp;</pre>
</div>
</div>
<p>The _feeds variable is a ObservableCollection&lt;SyndicationFeed&gt; in the above code.<br />
&nbsp;</p>
<div class="wlWriterHeaderFooter" style="padding-right: 4px; padding-left: 4px; padding-bottom: 4px; margin: 0px; padding-top: 4px; text-align: left"><a href="http://www.dotnetkicks.com/kick/?url=/data-services-with-silverlight-2/linq-to-rss-atom-kind-of/"><img alt="DotNetKicks Image" border="0" src="http://www.dotnetkicks.com/Services/Images/KickItImageGenerator.ashx?url=/data-services-with-silverlight-2/linq-to-rss-atom-kind-of/&amp;bgcolor=0080C0&amp;fgcolor=FFFFFF&amp;border=000000&amp;cbgcolor=D4E1ED&amp;cfgcolor=000000" /></a></div>
<div class="wlWriterHeaderFooter" style="padding-right: 4px; padding-left: 4px; padding-bottom: 4px; margin: 0px; padding-top: 4px; text-align: left"><script type="text/javascript">var dzone_url = '/data-services-with-silverlight-2/linq-to-rss-atom-kind-of/'; var dzone_title = 'LINQ to RSS/ATOM (Kind of)'; var dzone_blurb = 'LINQ to RSS/ATOM (Kind of)'; var dzone_style = '2';</script><script language="javascript" src="http://widgets.dzone.com/widgets/zoneit.js"></script></div>

