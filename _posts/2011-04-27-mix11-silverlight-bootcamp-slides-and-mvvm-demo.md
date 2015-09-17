---
layout: post
title: MIX11 Silverlight Bootcamp Slides and MVVM Demo
date: 2011-04-27 06:15
author: John
comments: true
categories: [guitarshop, mix11, mvvm, Silverlight]
---
<p>Mike Taulty and I hosted a 3.5 hour Silverlight bootcamp at MIX11 this year (Mike will be posting all of the slides and demos on his site soon, including mine. I&rsquo;ll link to it when it is up. For the record, I held him up <img src="/wp-content/uploads/media/Windows-Live-Writer/MIX11-Silverlight-Bootcamp-Slides-and-MV_13C1B/wlEmoticon-smile_2.png" alt="Smile" class="wlEmoticon wlEmoticon-smile" style="border-style: none;" /> .)</p>
<p>The topic for the last hour of the bootcamp was MVVM and &ldquo;Hooking Up&rdquo;. I demonstrated some quick tips on MVVM concepts and then walked through a scenario where Mike played the designer (who was actually my friend and colleague Arturo Toledo) and I played the developer. This was a real story where where Arturo and I worked through the MVVM demo in a matter of 3 days.&nbsp;</p>
<p><a href="/wp-content/uploads/media/Windows-Live-Writer/MIX11-Silverlight-Bootcamp-Slides-and-MV_13C1B/image_4.png"><img height="315" width="539" src="/wp-content/uploads/media/Windows-Live-Writer/MIX11-Silverlight-Bootcamp-Slides-and-MV_13C1B/image_thumb_1.png" alt="image" border="0" title="image" style="border-width: 0px; padding-top: 0px; padding-right: 0px; padding-left: 0px; display: inline; background-image: none;" /></a></p>
<p>The deck walks through the fundamentals of MVVM first and why abstraction and design time data are important. Then I begin the story and show how Arturo starts with wireframes, goes to visuals (pure graphics), and then to XAML. In the meantime I build the backend and the front end, using design time data that fits with my runtime data model and services. We collaborate as we go, and the result is that Arturo gives me the final XAML and I spend less than an hour putting it into my project and letting her rip.</p>
<p>I&rsquo;ll be discussing this process and expanding on this demo more in the coming weeks, but for now I wanted to get the basic demo out there along with the slides. So yes, I realize the code is not perfect, the XAMl is not perfect, but that&rsquo;s kind of the point. The back end and the design are solid. There is room for the XAMl to be cleaned up and other views and services to be added. I have since made a much cleaner and more expansive app (more views, viewmodels, navigation, etc), but for now let&rsquo;s stick with the core.</p>
<p><a href="/wp-content/uploads/media/Windows-Live-Writer/MIX11-Silverlight-Bootcamp-Slides-and-MV_13C1B/image_2.png"><img height="275" width="541" src="/wp-content/uploads/media/Windows-Live-Writer/MIX11-Silverlight-Bootcamp-Slides-and-MV_13C1B/image_thumb.png" alt="image" border="0" title="image" style="border-width: 0px; padding-top: 0px; padding-right: 0px; padding-left: 0px; display: inline; background-image: none;" /></a></p>
<p>Enjoy!</p>
<p>You can <a href="/wp-content/uploads/files/downloads/GuitarShop - MIX11 SL Bootcamp demo.zip">download rev 1 of the GuitarShop demo</a> and the <a href="/wp-content/uploads/files/downloads/mix11-mvvm.zip">MVVM / Hooking Up slides</a> here.</p>
<blockquote>
<p>Note that I removed all the guitar images and replaced them with the same image. I am working on verifying which images I can distribute in the demo. But in the meantime, all images will look like the same guitar, so don&rsquo;t be alarmed <img src="/wp-content/uploads/media/Windows-Live-Writer/MIX11-Silverlight-Bootcamp-Slides-and-MV_13C1B/wlEmoticon-smile_2.png" alt="Smile" class="wlEmoticon wlEmoticon-smile" style="border-style: none;" /></p>
</blockquote>
<p>Requirements for the demo:<br />- Visual Studio 2010 SP 1<br />- SqlServer Ce v4 <br />- Visual Studio 2010 tools for SqlServer Ce v4 <br />- Expression Samples PathListBoxUtils <br />- Silverlight 5 beta<br />- Expression Blend Preview for SL 5<br />- Entity Framework 4.1 (for code first)<br />- MVVM Light</p>

