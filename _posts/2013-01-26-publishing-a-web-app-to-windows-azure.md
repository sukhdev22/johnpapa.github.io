---
layout: post
title: Publishing a Web App to Windows Azure
date: 2013-01-26 04:09
author: John
comments: true
categories: [azure, Uncategorized, visual studio 2012]
---
Often I like to test my web apps in a real website. For me, Windows Azure is ideally suited for this. I can spin up a site as needed, publish my demo, test it on a variety of devices, and tear it down when I am done. the best part is that it only takes a few moments to learn how to do this. What do you need? Just install Visual Studio 2012 and open a Windows Azure account and you are all set. In this post I'll tell you how to set up an Azure website, how to publish to Azure, and offer several tips in case you run into issues along the way.

<a href="http://www.johnpapa.net/publishing-a-web-app-to-windows-azure/1-25-2013-11-04-02-pm/" rel="attachment wp-att-14321"><img src="http://www.johnpapa.net/wp-content/uploads/2013/01/1-25-2013-11-04-02-PM.png" alt="1-25-2013 11-04-02 PM" width="580" height="213" class="aligncenter size-full wp-image-14321" /></a>

<h2>At a Glance</h2>
In the Windows Azure Portal
<ul><li>Sign up for an account with Windows Azure</li>
<li>Create a New Web Site</li>
<li>Download the publishing profile file</li></ul>

In Visual Studio 2012
<ul><li>Ensure all NuGet packages are installed</li>
<li>Build your solution</li>
<li>Publish your solution</li></ul>

<h2>Create a Windows Azure Web Site</h2>
The first step is to <a href="http://www.windowsazure.com/" target="_blank">sign up and create an account with Windows Azure</a>. Depending on what programs you are participating in you may qualify for different options. I'll assume that you have signed up or can figure that out on your own. The next step is to create a web site in Azure. I don't require a lot of resources for testing my apps, so when I create web sites for this purpose I just choose the smallest/cheapest options available. That is what I will go through here.

<a href="https://manage.windowsazure.com" target="_blank">Go to your Windows Azure portal</a> and select the plus sign in the bottom left hand corner.
<a href="http://www.johnpapa.net/publishing-a-web-app-to-windows-azure/azure-new-site/" rel="attachment wp-att-14181"><img src="http://www.johnpapa.net/wp-content/uploads/2013/01/azure-new-site.png" alt="azure-new site" width="600" height="485" class="aligncenter size-full wp-image-14181" /></a>

Then choose the Web Site option, and the Quick Create option. From here, it will ask you to type in the url you want. It automatically places you in the azurewebsites.net domain. (You can reconfigure  this later if you want to use a domain that you own.) I typed in papademonstration so I get papademonstration.azurewebsites.net. I trust you will pick something far shorter :)

<a href="http://www.johnpapa.net/publishing-a-web-app-to-windows-azure/azure-quick-create/" rel="attachment wp-att-14211"><img src="http://www.johnpapa.net/wp-content/uploads/2013/01/azure-quick-create.png" alt="azure-quick create" width="550" height="170" class="aligncenter size-full wp-image-14211" /></a>

In my experience, it will take anywhere from 30 seconds to a few minutes to spin up the new site. When using the Quick Create you get a very simple setup. You can configure your domain name, whether you want to share a virtual server or get a reserved server, how many cores, instances, memory and so on. For this post, I'm just focusing on the simple route where you want to spin up a site so you can test your app, and for that the Quick Create is all I'll need.

<h2>Publishing Profile</h2>
Next you are going to want to know how to connect Visual Studio to Azure so you can publish your project to it. For this you will need the publishing profile. Once the web site's status says <code>running</code> instead of <code>creating ...</code>, click on the name of the web site in the Azure portal. You will then see the dashboard for that new site. On the right you will see a section titled <code>quick glance</code>. From here you can click the link to <code>download publish profile</code>.

<a href="http://www.johnpapa.net/publishing-a-web-app-to-windows-azure/azure-dashboard/" rel="attachment wp-att-14241"><img src="http://www.johnpapa.net/wp-content/uploads/2013/01/azure-dashboard.png" alt="azure-dashboard" width="308" height="274" class="aligncenter size-full wp-image-14241" /></a>

This will download the profile to your computer. It is a text file and if you open it you can see it contains sensitive information about connecting to your site.

<h2>Publish in Visual Studio</h2>
Next, go to Visual Studio 2012 and open your project. Be sure that all of the NuGet packages are installed properly and that you have just re-built the solution successfully. 

<blockquote>Tip: I have found that the publishing process goes much smoother when you build immediately prior to publishing.</blockquote>

While the project is selected, go to the Visual Studio 2012 menu and select Build and Publish.

<a href="http://www.johnpapa.net/publishing-a-web-app-to-windows-azure/publish/" rel="attachment wp-att-14251"><img src="http://www.johnpapa.net/wp-content/uploads/2013/01/publish.png" alt="publish" width="419" height="321" class="aligncenter size-full wp-image-14251" /></a>

You will see a dialog that allows you to import a profile. Click the import button and locate the publish profile you recently downloaded for your new web site. This is how you tell Visual Studio 2012 where to send your code. Then click the <code>next</code> button. I recommend clicking the <code>Validation Connection</code> button on the Connection dialog, just to verify it can communicate with the web site. Then click the <code>next</code> button and you will see the settings dialog, where you can choose which configuration to publish (release, debug, etc). Then click the <code>next</code> button again and yu will see the preview dialog. I recommend always coming to this dialog and click the <code>Start Preview</code> button. Sometime you will see "Preview Failed (click here for details)". Often the error message it reveals is obtuse, so I simply close this, save any changes to the profile, clean and rebuild the solution and try again. It often works after that. 


<blockquote>Tip: Don't be scared if you see a message that says "Web.config not found". I think there must be a random strange error message generator that kicks in when the preview fails. I just ignore those messages as they rarely make sense and rebuild the solution. The messages might as well say "pigs are flying out your window" for all the help they are.</blockquote>

Once you get a clean preview, you can click the <code>publish</code> button. All files are then sent up to the web site and it will open a browser and hopefully you will see your app!

<h2>Avoiding Gremlins</h2>
If you are like me, then you likely won't hit the happy path each time your publish. It's common for me to forget something and have to try again. Here are some more tips I have learned along the way that may help you if you read this far. If you didn't, well, then, I might as well do a dance since you aren't reading this far anyway. :)
<h5>Rebuild</h5>
Always rebuild right before you publish. Yes, i said it a few times in here, but it's very important to staving off gremlins.
<h5>Include Files</h5>
Remember to include files in your Visual Studio 2012 project that you want published. If you don't you can always FTP them later.
<h5>Restart Web Site</h5>
If you have problems publishing to your web site, go to the portal and restart the site. It takes about 5 seconds for me.
<h5>FTP</h5>
If you have problems publishing on top of existing files, consider FTP'ing to your site and clearing it manually. I had to do this once or twice myself.
<h5>Miss a File?</h5>
If a file did not get sent up to your web site, you can always FTP it. 
<h5>keep It Secret, Keep it Safe</h5>
Your FTP credentials are in the publish profile (you may want to make sure you protect that file).
<h5>SQL Server CE</h5>
If you publish a SQL Server CE file (an *.sdf) for use with EntityFramework, make sure you have the <a href="http://nuget.org/packages/EntityFramework.SqlServerCompact/4.3.6" target="_blank">EntityFramework.SqlServerCompact</a> NuGet package installed before you publish. Otherwise you may see errors trying to connect to the database.
<h5>What's the Real Error?</h5>
If you see obtuse error messages, turn off customErrors in web.config to reveal the real error message (then be sure to undo this later).
<pre class="prettyprint linenums">
<configuration>
    <system.web>
        <customErrors mode="Off"/>
    </system.web>
</configuration>
</pre>
<h5>Tear it Down</h2>
If you want to tear down your site, simply select your web site in the Azure portal and select the <code>delete</code> icon in the bottom menu. You can always spin a new one up later.
