---
layout: post
title: Walking Through the Orchard Part 1 - Setting up a Blog
date: 2011-04-25 07:16
author: John
comments: true
categories: [Graffiti, Orchard, SQL CE, Uncategorized, WebMatrix, WebPI]
---
I spent some time last week working on converting my blog that you  are reading at <a href="http://johnpapa.net">http://johnpapa.net</a> from Graffiti CMS to Orchard CMS 1.1.3. This post explains pretty much everything I had to do from beginning to end, so it is pretty lengthy. But it should be helpful to anyone moving from Graffiti to Orchard, or for that matter, moving from any blog to Orchard. In fact, after I went through the process once for my main blog, I used these same notes to convert another blog. I plan on 3 parts to this series, which this is the first.

This is Part 1 where I will cover how I used WebMatrix to install orchard and set up its initial settings, setup a theme, install some fundamental modules, and configure them.
<ul><li><a href="/orchardpart1">Walking Through the Orchard Part 1 – Setting up a Blog</a></li>
<li><a href="/orchardpart2">Walking Through the Orchard Part 2 – Conversion from Graffiti</a></li>
<li><a href="/orchardpart3">Walking Through the Orchard Part 3 – BlogML Import</a></li>
</ul>


<blockquote>NOTE: Quick callout to a few folks who helped me tremendously during this process. Much of what’s written in this series, while depictive of my experiences, is due to the help given by these folks. Because of them I can share this with all of you.</blockquote>
<blockquote>- Drew Robbins had gone through a conversion from WordPress and assisted me with the setup of Orchard, its modules and various questions along the way. He authored the FollowMe module and my theme.

- Sebastien Ros of the Orchard team helped with various key problems I ran into. The biggest of which you’ll find I wrote about in parts 2 and 3 of the series where rewrite rules and content display problems came into play. His quick responses were extremely helpful. He even published a brand new Rewrite Rules module while I was chatting with him, that fixed some of my problems.

-Scott Forsyth, of <a href="http://www.orcsweb.com/">ORCSweb Managed Hosting</a>, and his support team continued to give me the best support I have ever received from a hosting provider by a long stretch. These folks know their stuff, are quick to respond any time of day, and talk to me on my level (no talking down). Point blank: without ORCSweb’s support this would have been a much longer process.</blockquote>
<h2>Web Platform Installer</h2>
Before you get started, I recommend installing the <a href="http://www.microsoft.com/web/downloads/platform.aspx">Web Platform Installer</a>. I used it for WebMatrix, SQL Server CE and for Orchard CMS. It’s a quick install and really simplifies the process.
<h2>Setup of Orchard using WebMatrix</h2>
<a href="http://www.asp.net/WebMatrix">I used WebMatrix</a> to install Orchard and handle a few other tasks along the way. It really did simplify things so I highly recommend using it. Once installed, I ran WebMatrix and clicked on the button to create a new site from <strong>Web Gallery</strong>. I then search for orchard, entered the new site name (JohnPapa.net) and clicked the <strong>next </strong>button. This took about 15 seconds and I had a site up and running locally.

<a href="/wp-content/uploads/media/Windows-Live-Writer/5df882b575d3_12C4C/image_2.png"><img style="background-image: none; padding-left: 0px; padding-right: 0px; display: inline; padding-top: 0px; border-width: 0px;" title="image" src="/wp-content/uploads/media/Windows-Live-Writer/5df882b575d3_12C4C/image_thumb.png" alt="image" width="504" height="365" border="0" /></a>

The next step is to configure the settings for the site, which I did by clicking the link to the localhost url in WebMatrix. This brings up the new Orchard site’s Get Started page (shown below). I entered the name of the site, chose a user name for the admin user,   and a password. I chose to use a SQL Server CE database for the simplicity and portability of the sdf file. Then I also chose the blog Orchard Recipe type.
<blockquote>NOTE: If you choose SQL CE and want to migrate to SQL Express or SQL Server later you can.</blockquote>
<a href="/wp-content/uploads/media/Windows-Live-Writer/5df882b575d3_12C4C/image_8.png"><img style="background-image: none; padding-left: 0px; padding-right: 0px; display: inline; padding-top: 0px; border-width: 0px;" title="image" src="/wp-content/uploads/media/Windows-Live-Writer/5df882b575d3_12C4C/image_thumb_3.png" alt="image" width="504" height="721" border="0" /></a>

The recipe gets baked and within seconds the blog is appears in the browser using a default blog template.
<h2>Themes</h2>
Looks and layout are important, so the first place I headed was the Themes gallery. You can get there by going to the Dashboard, selecting the Themes section and selecting the Gallery tab. From here, I looked for themes that fit my idea of a blog. The Super Classic one is not bad.
<blockquote>Note: I am using a custom theme not in the gallery, for now.</blockquote>
<a href="/wp-content/uploads/media/Windows-Live-Writer/5df882b575d3_12C4C/SNAGHTML24adfc68.png"><img style="background-image: none; padding-left: 0px; padding-right: 0px; display: inline; padding-top: 0px; border-width: 0px;" title="SNAGHTML24adfc68" src="/wp-content/uploads/media/Windows-Live-Writer/5df882b575d3_12C4C/SNAGHTML24adfc68_thumb.png" alt="SNAGHTML24adfc68" width="504" height="362" border="0" /></a>

Once you find a theme you like, install it. Then click on the Themes / Installed tab and find the theme you want. Then click it’s <strong>Set Current </strong>button. The theme I chose has a side panel on the right where I planned to put my widgets (just like the Super Classic and Classic themes above). You can change themes at any time.
<h2>Orchard Modules</h2>
One of the best parts of Orchard is that they follow the model of many other popular blogs by allowing you to import modules to add functionality. The first thing I recommend doing is adding several key modules from the Orchard Gallery. Easiest way to do this is to go to your new blog’s Dashboard, select Modules, then select the Gallery tab. From here you can search for and install (or download and install) the modules.

<a href="/wp-content/uploads/media/Windows-Live-Writer/5df882b575d3_12C4C/SNAGHTML248594bf.png"><img style="background-image: none; padding-left: 0px; padding-right: 0px; display: inline; padding-top: 0px; border-width: 0px;" title="SNAGHTML248594bf" src="/wp-content/uploads/media/Windows-Live-Writer/5df882b575d3_12C4C/SNAGHTML248594bf_thumb.png" alt="SNAGHTML248594bf" width="504" height="221" border="0" /></a>
<blockquote>Note: Once you install a module, if there is an update for the module available in the online gallery then an alert will appear in your site in the module section. Nice feature!</blockquote>
I installed most modules right from this page. However, I found it easier to search the <a href="http://orchardproject.net/gallery">http://orchardproject.net/gallery</a> site online in some cases.

Here are the modules I added and some important notes for each:
<table width="570" border="0" cellspacing="1" cellpadding="1">
<tbody>
<tr>
<td valign="top" width="126">
<blockquote style="margin-right: 0px;" dir="ltr">
<p align="left"><strong>Module</strong></p>
</blockquote>
</td>
<td valign="top" width="439">
<blockquote style="margin-right: 0px;" dir="ltr">
<p align="left"><strong>Notes</strong></p>
</blockquote>
</td>
</tr>
<tr>
<td valign="top" width="126"><a href="http://orchardproject.net/gallery/List/Modules/Orchard.Module.NGM.BlogML">BlogML</a></td>
<td valign="top" width="439">I needed this module to import the BlogML file that I exported from Graffiti.</td>
</tr>
<tr>
<td valign="top" width="126"><a href="http://orchardproject.net/gallery/List/Modules/Orchard.Module.Contrib.GoogleAnalytics">Google Analytics</a></td>
<td valign="top" width="439">For Google analytics. Once installed, go to Settings and enter your analytics tracking ID. I installed the one from Nathan Heskew and Sebastien Ros (there are 2 with the same name <img class="wlEmoticon wlEmoticon-sadsmile" style="border-style: none;" src="/wp-content/uploads/media/Windows-Live-Writer/5df882b575d3_12C4C/wlEmoticon-sadsmile_2.png" alt="Sad smile" /> )</td>
</tr>
<tr>
<td valign="top" width="126"><a href="http://orchardproject.net/gallery/List/Modules/Orchard.Module.Contrib.RewriteRules">Rewrite Rules</a></td>
<td valign="top" width="439">I needed these to keep my old links pointing to the same content where url’s changed. More on this later</td>
</tr>
<tr>
<td valign="top" width="126"><a href="http://orchardproject.net/gallery/List/Modules/Orchard.Module.Orchard.Messaging">Messaging</a></td>
<td valign="top" width="439">Required by <strong>Email Messaging </strong>module</td>
</tr>
<tr>
<td valign="top" width="126"><a href="http://orchardproject.net/gallery/List/Modules/Orchard.Module.Orchard.Email">Email Messaging</a></td>
<td valign="top" width="439">Required for some other modules, like the <strong>Contact Us</strong> module. Once installed, go under Settings in the Dashboard and enter your information.</td>
</tr>
<tr>
<td valign="top" width="126"><a href="http://orchardproject.net/gallery/List/Modules/Orchard.Module.EWSNoggin.ContactUs">Contact Us</a></td>
<td valign="top" width="439">There are a couple of “contact” forms. This one was most simple for me to tweak.</td>
</tr>
<tr>
<td valign="top" width="126"><a href="http://orchardproject.net/gallery/List/Modules/Orchard.Module.Orchard.Indexing">Indexing</a></td>
<td valign="top" width="439">required for the <strong>Search </strong>module</td>
</tr>
<tr>
<td valign="top" width="126"><a href="http://orchardproject.net/gallery/List/Modules/Orchard.Module.Lucene">Lucene</a></td>
<td valign="top" width="439">recommended for the <strong>Search </strong>module</td>
</tr>
<tr>
<td valign="top" width="126"><a href="http://orchardproject.net/gallery/List/Modules/Orchard.Module.Orchard.Search">Search</a></td>
<td valign="top" width="439">For searching your site (I had issues with this one and the made the team aware. more on this later)</td>
</tr>
<tr>
<td valign="top" width="126"><a href="http://orchardproject.net/gallery/List/Modules/Orchard.Module.Drewby.FollowMe">FollowMe</a></td>
<td valign="top" width="439">Nice social module that allows you to add a small widget to your side panel with links to Twitter, Facebook, email, Linked In, or your RSS feed. A colleague of mine, Drew Robbins wrote this one.</td>
</tr>
<tr>
<td valign="top" width="126"><a href="http://orchardproject.net/gallery/List/Modules/Orchard.Module.LatestTwitter">LatestTwitter</a></td>
<td valign="top" width="439">One of a few Twitter modules. I liked this one because it was easy to template the display of the tweets in my side panel by changing its cshtml file.</td>
</tr>
</tbody>
</table>
<blockquote>Note: Once you install the modules there appears to be now way to remove them. However you can disable them. I did this when I tried some modules and found better ones.</blockquote>
There are many more modules, some which I already added and other that I plan to add soon. But these are the core ones I felt I needed just to get my blog up and running, so let’s start here. here are a few special notes regarding setup of some of these modules.

<strong>Email Messaging </strong>

For the <a href="http://orchardproject.net/gallery/List/Modules/Orchard.Module.Orchard.Email">Email Messaging</a> module I went to the Settings area in the Dashboard and found there were a few new settings sections for the new modules I installed. The Email settings required the sender’s email address, host name, port number, and credential information for my blog’s SMTP server.

<a href="/wp-content/uploads/media/Windows-Live-Writer/5df882b575d3_12C4C/image_6.png"><img style="background-image: none; padding-left: 0px; padding-right: 0px; display: inline; padding-top: 0px; border-width: 0px;" title="image" src="/wp-content/uploads/media/Windows-Live-Writer/5df882b575d3_12C4C/image_thumb_2.png" alt="image" width="237" height="484" border="0" /></a>

<strong>Contact Us</strong>

Once this module is installed and set up, you'll need to enable this module as it is disabled by default. Next, I went to the Contact Us section in the Dashboard and I added the recipient user name to be me. Then I went to the Users section in the Dashboard and edited my user, set it as an admin, and set the user’s email address. This was needed for the email modules I used. Without it, the <a href="http://orchardproject.net/gallery/List/Modules/Orchard.Module.EWSNoggin.ContactUs">Contact Us</a> module did not work (as it would not know where to send the messages).

a simple page was available at <a href="/contact">/contact</a> as shown below:

<a href="/wp-content/uploads/media/Windows-Live-Writer/5df882b575d3_12C4C/image_14.png"><img style="background-image: none; padding-left: 0px; padding-right: 0px; display: inline; padding-top: 0px; border-width: 0px;" title="image" src="/wp-content/uploads/media/Windows-Live-Writer/5df882b575d3_12C4C/image_thumb_6.png" alt="image" width="404" height="279" border="0" /></a>

<strong>Search</strong>

I debated whether including this or not, but since I feel search is pretty important on my site and I am still trying to get it to work I figured I’d share my experience anyway. <a href="http://orchardproject.net/gallery/List/Modules/Orchard.Module.Orchard.Search">Search</a> is a simple module as it allows me to include a widget in the side panel of my site to allow searching of content. It allows you to re-index the content on demand and allows you to select which fields the search will look at. All in all it looked great. In fact, it worked fine for a while but at some point it stopped working and instead of searching it brought up an odd page with search information and comments (like it was a blog post). I won’t go any further one what else it did wrong, but suffice to say I alerted the Orchard team and some folks there are looking into it. Hopefully its just something I did. I’ll report back on this either way.

<strong>Widgets</strong>

Next I wanted to set up my layout. The theme I chose had some sections filled in with placeholder content, which is nice since it gives you an idea of where things will appear. But of course you’ll want to remove those and add content where you want them to appear.  So I first went to the Widgets section in the Dashboard and removed the content I did not want to appear. Then I started working on my right side panel. For my theme this was the AsideSecond section. Here I added a series of widgets from top to bottom. You can add new widgets, re-adjust the order in which they appear, disable them, edit them, or remove them.

I added a Search widget here first, but later disabled it as it was not working consistently for me. I could have removed it, but again, I plan to put this back in later.

I then added an Html Widget which is great for adding any HTML content. In this case I added a small headshot of me and a few tiny images I wanted to appear on top. Next I added the Follow Me widget, then the Twitter widget, followed by a series of Html widgets for other content.

<strong>FollowMe</strong>

The <a href="http://orchardproject.net/gallery/List/Modules/Orchard.Module.Drewby.FollowMe">FollowMe</a> module was written by Drew Robbins and is a clean and simple module that adds something like this image:

<a href="/wp-content/uploads/media/Windows-Live-Writer/5df882b575d3_12C4C/image_10.png"><img style="background-image: none; margin: 0px; padding-left: 0px; padding-right: 0px; display: inline; padding-top: 0px; border-width: 0px;" title="image" src="/wp-content/uploads/media/Windows-Live-Writer/5df882b575d3_12C4C/image_thumb_4.png" alt="image" width="244" height="68" border="0" /></a>

When I added the widget, I edited its settings by entering the Twitter Url, Facebook Url, Rss Url, and Flickr Url. You can also add one for email and YouTube. I left these latter 2 blank, which made the widget not display them (which is what I wanted).
<blockquote>Note: You can add a title to the widgets, but I generally avoid this as I think it adds clutter to the panel.</blockquote>
Notice the widgets in the image below are displayed in gray when disabled. Also notice that many of the widgets say Html Widget (their type). I would prefer that I could add a title but mark it as hidden. This would allow me to see the name of the widget in the dashboard instead of seeing a ton of Html Widget types.

<a href="/wp-content/uploads/media/Windows-Live-Writer/5df882b575d3_12C4C/image_12.png"><img style="background-image: none; padding-left: 0px; padding-right: 0px; display: inline; padding-top: 0px; border-width: 0px;" title="image" src="/wp-content/uploads/media/Windows-Live-Writer/5df882b575d3_12C4C/image_thumb_5.png" alt="image" width="504" height="716" border="0" /></a>
<h2>LatestTwitter</h2>
I tried a few of the Twitter widgets and there are several nice ones. The one I ended up with is a simple widget with few features called <a href="http://orchardproject.net/gallery/List/Modules/Orchard.Module.LatestTwitter">LatestTwitter</a>. I like it because its pretty basic and does what I need yet allows me to customize the appearance.
<blockquote>Note: There is also a widget called <a href="http://orchardproject.net/gallery/List/Modules/Orchard.Module.Twitter">Twitter</a> which allows you to create a scrolling list of tweets, shows searches, and much more. I installed it and it works nice. I just did not need that for now.</blockquote>
<h2>Coming in Part 2 … Walking Through the Orchard Part 2 – Conversion from Graffiti</h2>
In Part 2 of this series I will walk through the export from Graffiti to BlogML and the import process from the BlogML file I created and all of the tweaks I made during the conversion. This included the import process, rewrite rules, and fixes due to conversion problems.
<h2>Coming in Part 3 … Walking Through the Orchard Part 3 – Fixes, Tips, and Performance</h2>
Then in Part 3 I’ll hit a few other changes I made and cover some tips and tricks. These included database migrations, webdeploy tips, IIS 6 and IIS 7 differences, content display problems, and performance.
