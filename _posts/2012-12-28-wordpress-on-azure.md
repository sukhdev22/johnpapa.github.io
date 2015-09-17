---
layout: post
title: Propping Up WordPress on Azure
date: 2012-12-28 20:16
author: John
comments: true
categories: [azure, cleardb, mysql, Uncategorized, wordpress]
---
Recently I moved <a href="http://johnpapa.net" target="_blank">my blog</a> to Azure's cloud. I had some free credits for <a href="http://www.windowsazure.com" target="_blank">Windows Azure</a> since I have an MSDN subscription, so I figured why not give it a shot.&nbsp;This move meant 3 big changes for me: Microsoft's Azure platform, <a href="https://www.cleardb.com" target="_blank">ClearDB</a>'s &nbsp;MySQL services, and making sure I understood the costs in advance. &nbsp;It has been 3 months and overall I'm thrilled with the platform for my blog. This post will show how quickly you can get a WordPress blog up and running.

Azure does a heckuva lot more than host a web site that uses WordPress. But to keep focused, this post will cover my tips for using Azure for WordPress only. My goals for my blog were simple: I want it to be simple and require very little maintenance on my part to keep it functional.
<h2>Creating a WordPress Site on Azure</h2>
Once you open an account with Windows Azure you can go to their portal to view the buffet of services and products you can purchase. I started by clicking the "New" button in the bottom left hand corner of he screen. This opens a dialog that gives you access to create everything that Azure offers.
<a href="http://www.johnpapa.net/wordpress-on-azure/azure-portal/" rel="attachment wp-att-12171"><img class="aligncenter size-large wp-image-12171" alt="azure portal" src="http://www.johnpapa.net/wp-content/uploads/2012/12/azure-portal-600x402.png" width="600" height="402" /></a>
Perhaps the easiest way to create a WordPress site is to use their gallery. Once you click the "New" button, choose the "Compute" menu option, then choose "Web Site", and "From Gallery".
<a href="http://www.johnpapa.net/wordpress-on-azure/azure-compute-web-site-from-gallery/" rel="attachment wp-att-12191"><img class="aligncenter size-full wp-image-12191" alt="azure - compute - web site - from gallery" src="http://www.johnpapa.net/wp-content/uploads/2012/12/azure-compute-web-site-from-gallery.png" width="586" height="282" /></a>
A new dialog will open with all of the apps that Azure offers. When it opens (it may take a few seconds) scroll down til you see WordPress. Then click the arrows in the wizard and configure your WordPress site.
<a href="http://www.johnpapa.net/wordpress-on-azure/azure-wizard-1/" rel="attachment wp-att-12271"><img class="aligncenter size-full wp-image-12271" alt="azure - wizard 1" src="http://www.johnpapa.net/wp-content/uploads/2012/12/azure-wizard-1.png" width="942" height="635" /></a>Notice that it currently uses WordPress v3.4 The latest is now 3.5, so you will want to upgrade once you get it installed. I expect Azure will update this soon too.
<a href="http://www.johnpapa.net/wordpress-on-azure/azure-wizard-2/" rel="attachment wp-att-12281"><img class="aligncenter size-full wp-image-12281" alt="azure - wizard 2" src="http://www.johnpapa.net/wp-content/uploads/2012/12/azure-wizard-2.png" width="976" height="638" /></a>The url is important here if you don't want your own domain name. It must be unique, so choose wisely.
<a href="http://www.johnpapa.net/wordpress-on-azure/azure-wizard-3/" rel="attachment wp-att-12291"><img class="aligncenter size-large wp-image-12291" alt="azure - wizard 3" src="http://www.johnpapa.net/wp-content/uploads/2012/12/azure-wizard-3-600x392.png" width="600" height="392" /></a>
If you see an error message about being over your MySQL quota, you need to cancel the wizard and either choose an existing MySQL database or go to the Azure Store and purchase another MySQL database service from ClearDB. Then, once you get a new MySQL instance, you can run the wizard again and it will appear in your pick list.

Purchasing via the Azure store is quite simple. Choose the New button in the bottom menu and choose <code>Store</code>. Then select <code>ClearDB MySQL Database</code>. You can choose a free instance (limited to 20MB and 4 connections), or a paid instance (1GB or more of space).
<h2>Essential Plug-Ins</h2>
Once you complete the wizard, Azure spins away and launches a blog on your site running WordPress! Then you can add your plug-ins, configure them, and choose a theme. There are tons of plug-ins you can choose from, but I'll offer a 6 I find very useful:
<ol>
	<li><span style="line-height: 13px;"><a href="http://wordpress.org/extend/plugins/akismet/" target="_blank">Askimet</a> - great for catching spam</span></li>
	<li><a href="http://wordpress.org/extend/plugins/si-captcha-for-wordpress/" target="_blank">SI Captcha</a> -&nbsp;anti-spam methods to WordPress items</li>
	<li><a href="http://wordpress.org/extend/plugins/configure-smtp/" target="_blank">Configure SMTP</a></li>
	<li><a href="http://wordpress.org/extend/plugins/contact-form-7/" target="_blank">Contact Form 7</a>&nbsp;- I have no idea what happened to 1-6, but 7 is a fine contact form</li>
	<li><a href="http://wordpress.org/extend/plugins/prettify-gc-syntax-highlighter/" target="_blank">Pretty GC Syntax Highlighter</a> - adds syntax highlighting in your posts using google prettify</li>
	<li><a href="http://wordpress.org/extend/plugins/jetpack/" target="_blank">Jet Pack</a> - like 20 plug-ins in 1, this contains a ton of extras for WordPress including site stats</li>
</ol>
<h2>Azure Site Options</h2>
<h5>Dashboard and Monitor</h5>
The dashboard view gives you a quick glance at your site, its linked resources (like MySQL databases), your FTP host name, connection strings, options to reset credentials, set up git publishing, and more. It also has a link to your publishing profile, which you can use from Visual Studio. The monitor view shows you stats about CPU time, data usage, requests and errors.
<h5>Configure</h5>
The configure view allows you to add domain names, define connection strings, change your .NET framework or PHP version, and turn on server level settings. I wanted to use my domain name <code>www.johnpapa.net</code> with my blog. This feature was recently added to Azure so it was quite simple to do this. To get there I selected my site <code>johnpapa</code> from the portal.which brought me to my dashboard for the site. Then I clicked the <code>Configure</code> menu option at the top. From here, I clicked the <code>Manage Domains</code> button in the bottom menu and was able to add my domains in there. You simply type in your domain name(s). It also tells you the IP address that you ned to use when configuring your A records with your DNS hosting service. Be sure to do that or the domain won't be directed here.
<h5>Scale</h5>
The scale view allows you to change from a free to shared to reserved server if you need more power. This is pretty cool on how quickly it migrates everything for you in seconds, in my case. I was quite impressed by this. You can also choose your instance size (how many cores and memory do you need) as well as your instance count. This page as much as anything will dictate your costs. I chose to use the most powerful I could get and still stay within my free instance (using the MSDN Universal promotion).
<h5>Linked Resources</h5>
The final view is the linked resources. This is where you can see other services like the MySQL database that your WordPress blog uses. It is totally not obvious here, but that instance is not hosted by Azure but instead by ClearDB. Not that you really care where it is, as long as it is available. Still, it would be nice to know who to ask for support of it.
<h2>Summary</h2>
Creating the WordPress site was easy. In fact, it was up and running in just a few minutes. As simple as it was, there are a few important notes that I want to reiterate that may or may not be totally obvious.

The MySQL database that you get when you go through the gallery wizard to create the WordPress site has a 20MB limit, though it's not displayed anywhere during the wizard process nor on the dashboard. When you hit the limit ClearDB will turn off INSERT and UPDATE permissions on your database tables. This will cause terrible errors to show up on your site about permission problems. So the key here is to monitor your database size and keep it in check, or purchase a new larger database for your instance. If you do hit this, please <a href="http://johnpapa.net/azurecleardbmysql" target="_blank">see my follow-up post on tips on how to proactively or reactively fix this</a>.
