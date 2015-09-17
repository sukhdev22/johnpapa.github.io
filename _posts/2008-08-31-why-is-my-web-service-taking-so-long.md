---
layout: post
title: Why is My Web Service Taking so Long?
date: 2008-08-31 23:45
author: John
comments: true
categories: [All]
---
<p></p>  <p></p>  <p>Sometimes we are victims of our own cleverness. I could not figure out why my web service call was taking so long. After all, the service was local, the data was a simple query to the local database, and the response was tiny. So what’s the deal? Then I found this in my code in the DownloadStringCompleted event handler:</p>  <div>   <div style="padding-right: 0px; padding-left: 0px; font-size: 8pt; padding-bottom: 0px; overflow: visible; width: 100%; color: black; border-top-style: none; line-height: 12pt; padding-top: 0px; font-family: consolas, &#39;Courier New&#39;, courier, monospace; border-right-style: none; border-left-style: none; background-color: #f4f4f4; border-bottom-style: none">     <pre style="padding-right: 0px; padding-left: 0px; font-size: 8pt; padding-bottom: 0px; margin: 0em; overflow: visible; width: 100%; color: black; border-top-style: none; line-height: 12pt; padding-top: 0px; font-family: consolas, &#39;Courier New&#39;, courier, monospace; border-right-style: none; border-left-style: none; background-color: white; border-bottom-style: none">System.Threading.Thread.Sleep(5000);</pre>
</div>
</div>
<div>&#160;</div>
<div>Ugh! This was some code I had written during a demo that got copied and pasted into my code sample for my book somehow. I have been taking bits and pieces of code I have written and working them into examples. At one point I wanted to test some features when events were taking too long, so I faked it out with the Sleep method. </div>
<div>&#160;</div>
<div>Anyway, problem solved, crisis averted … until next time!</div><div class="wlWriterHeaderFooter" style="text-align:left; margin:0px; padding:4px 4px 4px 4px;"><a href="http://www.dotnetkicks.com/kick/?url=/all/why-is-my-web-service-taking-so-long/"><img src="http://www.dotnetkicks.com/Services/Images/KickItImageGenerator.ashx?url=/all/why-is-my-web-service-taking-so-long/&amp;bgcolor=0080C0&amp;fgcolor=FFFFFF&amp;border=000000&amp;cbgcolor=D4E1ED&amp;cfgcolor=000000" alt="DotNetKicks Image" border="0/"></a></div><div class="wlWriterHeaderFooter" style="text-align:left; margin:0px; padding:4px 4px 4px 4px;"><script type="text/javascript"><!-- var dzone_url = '/all/why-is-my-web-service-taking-so-long/'; var dzone_title = 'Why is My Web Service Taking so Long?'; var dzone_blurb = 'Why is My Web Service Taking so Long?'; var dzone_style = '1'; --></script><script language="javascript" src="http://widgets.dzone.com/widgets/zoneit.js"></script> </div>

