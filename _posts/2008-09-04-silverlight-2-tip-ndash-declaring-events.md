---
layout: post
title: Silverlight 2 Tip – Declaring Events
date: 2008-09-04 16:30
author: John
comments: true
categories: [Silverlight]
---
<p>&nbsp;</p>
<p>I&rsquo;ve seen a lot of demo&rsquo;s and example on Silverlight 2 flying around. One are that seems to get a lot of difference of opinion is where to declare events. You can either define the event handler in XAML declaratively, or you can add the handler in the .NET code. What&rsquo;s the best way?</p>
<p>Proponents of declaring the event handler in the XAML say anything that&rsquo;s static should go in the XAML. So let&rsquo;s run with that &hellip; let&rsquo;s assume that the event handler needs to be added and that it won&rsquo;t be removed and re-added (like you can do with code). Because obviously if that is the case, code is the place to do it. So we have this event handler declared in XAML, the upside is that its less code. Another upside is that its easy to do &hellip; just click on the properties in Blend and add the handler to the XAML.</p>
<p>But the downside is that functionality is now in the XAML. The XAML is often stated to be the place where designers can roam free. Are designers responsible for event handlers? I would say no, that&rsquo;s for the developer. If you subscribe to the theory that XAML is where the content and design should live, not functionality. So one day you are working on your .NET code and you are wondering why an event is getting invoked. Now you have to look in the code file as well as the XAML file (when you declare events in the XAML).</p>
<p>Adding the event in the code adds more physical code to the process, but the upside is that all of the functionality remains in the code file. If you put all of the handler definitions in the constructor as a group, then all of them are easy to find when working with the code.</p>
<p>What&rsquo;s my opinion? I firmly believe the handlers belong in the code and not in the XAML. I recommend putting the handlers in the code as a group, as shown below:</p>
<p><strong>C#</strong></p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<div>
<div style="padding-right: 0px; padding-left: 0px; font-size: 8pt; padding-bottom: 0px; overflow: visible; width: 100%; color: black; border-top-style: none; line-height: 12pt; padding-top: 0px; font-family: consolas, 'Courier New', courier, monospace; border-right-style: none; border-left-style: none; background-color: #f4f4f4; border-bottom-style: none">
<pre style="padding-right: 0px; padding-left: 0px; font-size: 8pt; padding-bottom: 0px; margin: 0em; overflow: visible; width: 100%; color: black; border-top-style: none; line-height: 12pt; padding-top: 0px; font-family: consolas, 'Courier New', courier, monospace; border-right-style: none; border-left-style: none; background-color: white; border-bottom-style: none"><span style="color: #0000ff">public</span> BookSearch()</pre>
<pre style="padding-right: 0px; padding-left: 0px; font-size: 8pt; padding-bottom: 0px; margin: 0em; overflow: visible; width: 100%; color: black; border-top-style: none; line-height: 12pt; padding-top: 0px; font-family: consolas, 'Courier New', courier, monospace; border-right-style: none; border-left-style: none; background-color: #f4f4f4; border-bottom-style: none">
{</pre>
<pre style="padding-right: 0px; padding-left: 0px; font-size: 8pt; padding-bottom: 0px; margin: 0em; overflow: visible; width: 100%; color: black; border-top-style: none; line-height: 12pt; padding-top: 0px; font-family: consolas, 'Courier New', courier, monospace; border-right-style: none; border-left-style: none; background-color: white; border-bottom-style: none">
InitializeComponent();</pre>
<pre style="padding-right: 0px; padding-left: 0px; font-size: 8pt; padding-bottom: 0px; margin: 0em; overflow: visible; width: 100%; color: black; border-top-style: none; line-height: 12pt; padding-top: 0px; font-family: consolas, 'Courier New', courier, monospace; border-right-style: none; border-left-style: none; background-color: #f4f4f4; border-bottom-style: none">
&nbsp;</pre>
<pre style="padding-right: 0px; padding-left: 0px; font-size: 8pt; padding-bottom: 0px; margin: 0em; overflow: visible; width: 100%; color: black; border-top-style: none; line-height: 12pt; padding-top: 0px; font-family: consolas, 'Courier New', courier, monospace; border-right-style: none; border-left-style: none; background-color: white; border-bottom-style: none">
btnOK.Click += <span style="color: #0000ff">new</span> RoutedEventHandler(btnOK_Click);</pre>
<pre style="padding-right: 0px; padding-left: 0px; font-size: 8pt; padding-bottom: 0px; margin: 0em; overflow: visible; width: 100%; color: black; border-top-style: none; line-height: 12pt; padding-top: 0px; font-family: consolas, 'Courier New', courier, monospace; border-right-style: none; border-left-style: none; background-color: #f4f4f4; border-bottom-style: none">
btnAddToCard.Click += <span style="color: #0000ff">new</span> RoutedEventHandler(btnAddToCard_Click);</pre>
<pre style="padding-right: 0px; padding-left: 0px; font-size: 8pt; padding-bottom: 0px; margin: 0em; overflow: visible; width: 100%; color: black; border-top-style: none; line-height: 12pt; padding-top: 0px; font-family: consolas, 'Courier New', courier, monospace; border-right-style: none; border-left-style: none; background-color: white; border-bottom-style: none">
btnClearCart.Click += <span style="color: #0000ff">new</span> RoutedEventHandler(btnClearCart_Click);</pre>
<pre style="padding-right: 0px; padding-left: 0px; font-size: 8pt; padding-bottom: 0px; margin: 0em; overflow: visible; width: 100%; color: black; border-top-style: none; line-height: 12pt; padding-top: 0px; font-family: consolas, 'Courier New', courier, monospace; border-right-style: none; border-left-style: none; background-color: #f4f4f4; border-bottom-style: none">
btnRemoveItem.Click += <span style="color: #0000ff">new</span> RoutedEventHandler(btnRemoveItem_Click);</pre>
<pre style="padding-right: 0px; padding-left: 0px; font-size: 8pt; padding-bottom: 0px; margin: 0em; overflow: visible; width: 100%; color: black; border-top-style: none; line-height: 12pt; padding-top: 0px; font-family: consolas, 'Courier New', courier, monospace; border-right-style: none; border-left-style: none; background-color: white; border-bottom-style: none">
&nbsp;</pre>
<pre style="padding-right: 0px; padding-left: 0px; font-size: 8pt; padding-bottom: 0px; margin: 0em; overflow: visible; width: 100%; color: black; border-top-style: none; line-height: 12pt; padding-top: 0px; font-family: consolas, 'Courier New', courier, monospace; border-right-style: none; border-left-style: none; background-color: #f4f4f4; border-bottom-style: none">
ShoppingCart = <span style="color: #0000ff">new</span> Cart();</pre>
<pre style="padding-right: 0px; padding-left: 0px; font-size: 8pt; padding-bottom: 0px; margin: 0em; overflow: visible; width: 100%; color: black; border-top-style: none; line-height: 12pt; padding-top: 0px; font-family: consolas, 'Courier New', courier, monospace; border-right-style: none; border-left-style: none; background-color: white; border-bottom-style: none">
}</pre>
</div>
</div>
<p>&nbsp;</p>
<p><strong>VB</strong></p>
<div>
<div style="padding-right: 0px; padding-left: 0px; font-size: 8pt; padding-bottom: 0px; overflow: visible; width: 100%; color: black; border-top-style: none; line-height: 12pt; padding-top: 0px; font-family: consolas, 'Courier New', courier, monospace; border-right-style: none; border-left-style: none; background-color: #f4f4f4; border-bottom-style: none">
<pre style="padding-right: 0px; padding-left: 0px; font-size: 8pt; padding-bottom: 0px; margin: 0em; overflow: visible; width: 100%; color: black; border-top-style: none; line-height: 12pt; padding-top: 0px; font-family: consolas, 'Courier New', courier, monospace; border-right-style: none; border-left-style: none; background-color: white; border-bottom-style: none"><span style="color: #0000ff">Public</span> <span style="color: #0000ff">Sub</span> <span style="color: #0000ff">New</span>()</pre>
<pre style="padding-right: 0px; padding-left: 0px; font-size: 8pt; padding-bottom: 0px; margin: 0em; overflow: visible; width: 100%; color: black; border-top-style: none; line-height: 12pt; padding-top: 0px; font-family: consolas, 'Courier New', courier, monospace; border-right-style: none; border-left-style: none; background-color: #f4f4f4; border-bottom-style: none">
InitializeComponent()</pre>
<pre style="padding-right: 0px; padding-left: 0px; font-size: 8pt; padding-bottom: 0px; margin: 0em; overflow: visible; width: 100%; color: black; border-top-style: none; line-height: 12pt; padding-top: 0px; font-family: consolas, 'Courier New', courier, monospace; border-right-style: none; border-left-style: none; background-color: white; border-bottom-style: none">
<span style="color: #0000ff">AddHandler</span> btnOK.Click, <span style="color: #0000ff">AddressOf</span> btnOK_Click</pre>
<pre style="padding-right: 0px; padding-left: 0px; font-size: 8pt; padding-bottom: 0px; margin: 0em; overflow: visible; width: 100%; color: black; border-top-style: none; line-height: 12pt; padding-top: 0px; font-family: consolas, 'Courier New', courier, monospace; border-right-style: none; border-left-style: none; background-color: #f4f4f4; border-bottom-style: none">
<span style="color: #0000ff">AddHandler</span> btnAddToCard.Click, <span style="color: #0000ff">AddressOf</span> btnAddToCard_Click</pre>
<pre style="padding-right: 0px; padding-left: 0px; font-size: 8pt; padding-bottom: 0px; margin: 0em; overflow: visible; width: 100%; color: black; border-top-style: none; line-height: 12pt; padding-top: 0px; font-family: consolas, 'Courier New', courier, monospace; border-right-style: none; border-left-style: none; background-color: white; border-bottom-style: none">
<span style="color: #0000ff">AddHandler</span> btnClearCart.Click, <span style="color: #0000ff">AddressOf</span> btnClearCart_Click</pre>
<pre style="padding-right: 0px; padding-left: 0px; font-size: 8pt; padding-bottom: 0px; margin: 0em; overflow: visible; width: 100%; color: black; border-top-style: none; line-height: 12pt; padding-top: 0px; font-family: consolas, 'Courier New', courier, monospace; border-right-style: none; border-left-style: none; background-color: #f4f4f4; border-bottom-style: none">
<span style="color: #0000ff">AddHandler</span> btnRemoveItem.Click, <span style="color: #0000ff">AddressOf</span> btnRemoveItem_Click</pre>
<pre style="padding-right: 0px; padding-left: 0px; font-size: 8pt; padding-bottom: 0px; margin: 0em; overflow: visible; width: 100%; color: black; border-top-style: none; line-height: 12pt; padding-top: 0px; font-family: consolas, 'Courier New', courier, monospace; border-right-style: none; border-left-style: none; background-color: white; border-bottom-style: none">
&nbsp;</pre>
<pre style="padding-right: 0px; padding-left: 0px; font-size: 8pt; padding-bottom: 0px; margin: 0em; overflow: visible; width: 100%; color: black; border-top-style: none; line-height: 12pt; padding-top: 0px; font-family: consolas, 'Courier New', courier, monospace; border-right-style: none; border-left-style: none; background-color: #f4f4f4; border-bottom-style: none">
ShoppingCart = <span style="color: #0000ff">New</span> Cart()</pre>
<pre style="padding-right: 0px; padding-left: 0px; font-size: 8pt; padding-bottom: 0px; margin: 0em; overflow: visible; width: 100%; color: black; border-top-style: none; line-height: 12pt; padding-top: 0px; font-family: consolas, 'Courier New', courier, monospace; border-right-style: none; border-left-style: none; background-color: white; border-bottom-style: none"><span style="color: #0000ff">End</span> Sub</pre>
</div>
</div>
<div class="wlWriterHeaderFooter" style="padding-right: 4px; padding-left: 4px; padding-bottom: 4px; margin: 0px; padding-top: 4px; text-align: left"><a href="http://www.dotnetkicks.com/kick/?url=/all/silverlight-2-tip-ndash-declaring-events/"><img alt="DotNetKicks Image" border="0" src="http://www.dotnetkicks.com/Services/Images/KickItImageGenerator.ashx?url=/all/silverlight-2-tip-ndash-declaring-events/&amp;bgcolor=0080C0&amp;fgcolor=FFFFFF&amp;border=000000&amp;cbgcolor=D4E1ED&amp;cfgcolor=000000" /></a></div>
<div class="wlWriterHeaderFooter" style="padding-right: 4px; padding-left: 4px; padding-bottom: 4px; margin: 0px; padding-top: 4px; text-align: left"><script type="text/javascript"><!-- var dzone_url = '/all/silverlight-2-tip-ndash-declaring-events/'; var dzone_title = 'Silverlight 2 Tip – Declaring Events'; var dzone_blurb = 'Silverlight 2 Tip – Declaring Events'; var dzone_style = '1'; --></script><script language="javascript" src="http://widgets.dzone.com/widgets/zoneit.js"></script></div>

