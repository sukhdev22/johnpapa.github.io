---
layout: post
title: SyndicationFeed and Silverlight 2 – Thanks FeedBurner
date: 2008-09-17 01:42
author: John
comments: true
categories: [Silverlight]
---
<p>I was writing a sample application tonight for my book (which is getting very close to being done!!!) that reads a RSS/ATOM feed, loads the results into the SyndicationFeed class and binds them to a Silverlight UI. Pretty straightforward really &hellip; but still very cool. So I hit the FeedBurner Uri for my site&rsquo;s RSS feed and it loads. Hey wait a second! I am going across domains so I should get a 404 not found error, right? Hold on a second John &hellip; I am hitting FeedBurner, remember? They have a crossdomain.xml file on teir site that allows full access, so its all good.</p>
<p>For a moment I thought I was hitting my site&rsquo;s RSS feed that I host and not the feedburner Uri. If I was hitting my personal site&rsquo;s feed, I would have actually gotten the 404 error since I do not have a cross domain file on the site yet.</p>
<p>So for once I expected to hit the cross domain issue but I was pleasantly surprised not to :)</p>
<p><img title="image" style="border-right: 0px; border-top: 0px; border-left: 0px; border-bottom: 0px" height="420" alt="image" width="507" border="0" src="/wp-content/uploads/files/media/image/WindowsLiveWriter/80d9726780b4_163E/image_3.png" /></p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>I love the SyndicationFeed class &hellip; anyone who has parsed feed data using an XmlReader feels the pain. LINQ to XML is a great alternative too.</p>
<div class="wlWriterHeaderFooter" style="padding-right: 4px; padding-left: 4px; padding-bottom: 4px; margin: 0px; padding-top: 4px; text-align: left"><a href="http://www.dotnetkicks.com/kick/?url=/data-services-with-silverlight-2/syndicationfeed-and-silverlight-2-ndash-thanks-feedburner/"><img alt="DotNetKicks Image" border="0" src="http://www.dotnetkicks.com/Services/Images/KickItImageGenerator.ashx?url=/data-services-with-silverlight-2/syndicationfeed-and-silverlight-2-ndash-thanks-feedburner/&amp;bgcolor=0080C0&amp;fgcolor=FFFFFF&amp;border=000000&amp;cbgcolor=D4E1ED&amp;cfgcolor=000000" /></a></div>
<div class="wlWriterHeaderFooter" style="padding-right: 4px; padding-left: 4px; padding-bottom: 4px; margin: 0px; padding-top: 4px; text-align: left"><script type="text/javascript">var dzone_url = '/data-services-with-silverlight-2/syndicationfeed-and-silverlight-2-ndash-thanks-feedburner/'; var dzone_title = 'SyndicationFeed and Silverlight 2 – Thanks FeedBurner'; var dzone_blurb = 'SyndicationFeed and Silverlight 2 – Thanks FeedBurner'; var dzone_style = '2';</script><script language="javascript" src="http://widgets.dzone.com/widgets/zoneit.js"></script></div>

