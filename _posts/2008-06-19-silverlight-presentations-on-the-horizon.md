---
layout: post
title: Silverlight Presentations On the Horizon
date: 2008-06-19 01:01
author: John
comments: true
categories: [All]
---
<p></p>  <p>I am sitting down writing about WCF interaction with Silverlight, cross domain issues, and other fun communication stuff. As I am drumming through these examples for the book and for some articles and presentations (phew) I am running into minor issues that really cause me to think differently about how to tackle them. For example, I wanted to produce a model popup window in Silverlight. Sure, no problem, I’ll just use the … wait … there is no modal popup control. There is a popup control, but its not modal. And it lacks a bit of refinement. I see from my friend Mr Google that others have tackled this issue in various ways … such as …</p>  <p>- Creating an abstract class that derives from the ContentControl and implementing methods that render the popup</p>  <p>- Creating a popup control inline in code, and restricting keyboard and mouse movement beyond the popup control</p>  <p>For now, since I could not find an elegant solution that I could fall in love with, I decided to create a popup control in a user control and expose custom properties on the user control so I could tweak the popup control and simulate modality. The user control has a canvas that stretches out over the base Silverlight control with a 50% opacity. This simulates a graying out of the background when the popup control appears and prevents mouse interaction. It does not prevent tabbing back into the originating Silverlight application, but that;s next on my list.&#160; It ain’t perfect, but it works good enough for now. I have to think that there will be an easier way to simulate modality in the future, at least by RTM.</p>  <p>Anyway … this and other issues like it got me to thinking that it might be a good thing to present some of these issues I am running into on my blog in narrative form like this post, in code samples, and in camtasia vdeos. I’ve got plenty to share … the only catch is finding the time between my main job, my speaking schedule, and my writing schedule and leave time for the family. The same ol’ battle :) But I think I will have some time to do some quick videos and postings on these topics so here’s my vow to share some of my Silverlight adventures, both successful and unsuccessful, in the coming weeks and months. The first will likely be on the modal popup that I described in this post. My hopes are that this sharing process will help refine some of these bumps in the road for Silverlight junkies like me.</p><div class="wlWriterHeaderFooter" style="text-align:left; margin:0px; padding:4px 4px 4px 4px;"><a href="http://www.dotnetkicks.com/kick/?url=/all/silverlight-presentations-on-the-horizon/"><img src="http://www.dotnetkicks.com/Services/Images/KickItImageGenerator.ashx?url=/all/silverlight-presentations-on-the-horizon/&amp;bgcolor=0080C0&amp;fgcolor=FFFFFF&amp;border=000000&amp;cbgcolor=D4E1ED&amp;cfgcolor=000000" border="0/"></a></div><div class="wlWriterHeaderFooter" style="text-align:left; margin:0px; padding:4px 4px 4px 4px;"><script type="text/javascript">var dzone_url = '/all/silverlight-presentations-on-the-horizon/';</script><script type="text/javascript">var dzone_title = 'Silverlight Presentations On the Horizon';</script><script type="text/javascript">var dzone_blurb = 'Silverlight Presentations On the Horizon';</script><script type="text/javascript">var dzone_style = '1';</script><script language="javascript" src="http://widgets.dzone.com/widgets/zoneit.js"></script> </div>
