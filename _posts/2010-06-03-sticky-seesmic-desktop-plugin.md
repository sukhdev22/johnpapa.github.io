---
layout: post
title: Sticky Seesmic Desktop Plugin
date: 2010-06-03 04:13
author: John
comments: true
categories: [Silverlight]
---
<blockquote>
<p><strong><font color="#ff0000">UPDATE</font>:</strong> I&rsquo;ve created a permanent home for the latest updates for Sticky. Please redirect&nbsp;<a href="http://jpapa.me/cXQ8yq">here</a> to stay updated on the latest versions, enhancements, and how to&rsquo;s for Sticky.</p>
</blockquote>
<p>&nbsp;</p>
<hr />
<p>I&rsquo;ve created a simple plugin named &ldquo;Sticky&rdquo; for Seesmic Desktop that I am sharing. <strong><a href="http://platform.seesmic.com/">Seesmic&rsquo;s Desktop Platform</a></strong> enables software developers to enhance the Seesmic Desktop application pretty easily, since is is built upon <a href="http://www.silverlight.net">Silverlight</a> 4 and uses MEF.</p>
<p><img style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="stickyProfile_rect" border="0" alt="stickyProfile_rect" width="80" height="28" src="/wp-content/uploads/files/media/image/WindowsLiveWriter/0267d1f5fe38_1515F/stickyProfile_rect_3.png" /></p>
<p>Feel free to use this plugin as you like. It is a simple plug in t<img style="border-right-width: 0px; margin: 5px 0px 0px 5px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="image" border="0" alt="image" align="right" width="241" height="238" src="/wp-content/uploads/files/media/image/WindowsLiveWriter/0267d1f5fe38_1515F/image_11.png" />hat, shows information about the Twitter user right inline with the Tweet. This post will explain what the Sticky plugin does and of course I&rsquo;ll share the plugin with you. I&rsquo;ll follow up with another post to explain how to create a plugin using the Seesmic Desktop platform, Visual Studio 2010, and Expression Blend.</p>
<p>If you want to learn more about the Seesmic Desktop Platform, here are some great links:</p>
<ul>
<li>The main <a href="http://platform.seesmic.com/">Seesmic Desktop Platform web page</a></li>
<li>the <a href="http://devwiki.seesmic.com">developer wiki</a></li>
<li><a href="http://devwiki.seesmic.com/Getting-Started-with-the-Desktop-Plugin-SDK">Creating your first Desktop Plugin</a></li>
<li><a href="http://groups.google.com/group/seesmic-desktop-dev">Developer discussion groups</a></li>
</ul>
<h3>Watch &ldquo;Sticky&rdquo; In Action</h3>
<p>Here is a <a href="http://www.youtube.com/watch?v=iaj8159npCI">quick video</a> showing the plugin in action.</p>
<div style="padding-bottom: 0px; margin: 0px auto; padding-left: 0px; width: 425px; padding-right: 0px; display: block; float: none; padding-top: 0px" id="scid:5737277B-5D6D-4f48-ABFC-DD9C333F4C5D:3f4ba7be-cb59-4a25-9f00-e85ad3a8c94a" class="wlWriterEditableSmartContent">
<div><object width="425" height="355"><param name="movie" value="http://www.youtube.com/v/iaj8159npCI&amp;hl=en&amp;fs=1&amp;hl=en"></param><embed src="http://www.youtube.com/v/iaj8159npCI&amp;hl=en&amp;fs=1&amp;hl=en" type="application/x-shockwave-flash" width="425" height="355"></embed></object></div>
</div>
<h3>Collapsed State</h3>
<p>When the Sticky plugin is in its collapsed state you will see a small icon for the plugin and a summary of the Twitter user&rsquo;s information (see below). It shows the number of Twitter followers, the number of friends and the number of updates for a Twitter user. <img style="border-right-width: 0px; display: block; float: none; border-top-width: 0px; border-bottom-width: 0px; margin-left: auto; border-left-width: 0px; margin-right: auto" title="image" border="0" alt="image" width="297" height="289" src="/wp-content/uploads/files/media/image/WindowsLiveWriter/0267d1f5fe38_1515F/image_12.png" /></p>
<p>&nbsp;</p>
<p>Here is a zoomed in close up of this information and the icon. When creating an icon you can customize the collapsed text as makes sense for your plugin. <img style="border-right-width: 0px; display: block; float: none; border-top-width: 0px; border-bottom-width: 0px; margin-left: auto; border-left-width: 0px; margin-right: auto" title="image" border="0" alt="image" width="350" height="72" src="/wp-content/uploads/files/media/image/WindowsLiveWriter/0267d1f5fe38_1515F/image_13.png" /></p>
<p>&nbsp;</p>
<h3>Expanded State</h3>
<p>In its expanded state, the Sticky plugin hides the collapsed view and transitions to a larger view. The expanded state shows the user&rsquo;s friendly name, a link to their web page, a link to the TwitterCounter for the user, a link to their Twitter page, and the user&rsquo;s Twitter profile bio (see below).</p>
<p><img style="border-right-width: 0px; display: block; float: none; border-top-width: 0px; border-bottom-width: 0px; margin-left: auto; border-left-width: 0px; margin-right: auto" title="image" border="0" alt="image" width="294" height="348" src="/wp-content/uploads/files/media/image/WindowsLiveWriter/0267d1f5fe38_1515F/image_16.png" /></p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>I used some visual states to subtly animate the sticky note when you move your mouse over it. This is a pretty simple use of visual states, easing, and effects which I&rsquo;ll explore in an upcoming post when I dive into the details of how the plug in is created.</p>
<h3>Get It</h3>
<p>You can download this plugin from the link below. Feel free to use it as you like. No warranties are provided, use it at your own risk ;-). It comes with the &ldquo;works on my machine&rdquo; status.</p>
<ul>
<li><a href="http://jpapa.me/cW3iMB">Download the Sticky plugin</a> now</li>
</ul>
<h3>Install It</h3>
<p>For now, the simplest way to install a plugin for Seesmic Desktop 2 is to copy and paste the plugin&rsquo;s xap file into the appropriate folder:</p>
<ul>
<li><strong>Windows</strong>: &quot;My Documents\Seesmic\Seesmic Desktop 2\Plugins&quot;</li>
<li><strong>Windows 7</strong>: &quot;Documents\Seesmic\Seesmic Desktop 2\Plugins&quot;</li>
<li><strong>Mac</strong>: &quot;$HOME\Documents\Seesmic\Seesmic Desktop 2\Plugins&quot;</li>
</ul>
<h3>How to</h3>
<p>I&rsquo;ll be posting how to create a plug in, some things to look out for, how to hook into the plugin using MEF, and some additional options that I did not exploit in this plugin. I&rsquo;ll also show how to create the Sticky note&rsquo;s look and feel in a post coming to this blog soon.</p>

