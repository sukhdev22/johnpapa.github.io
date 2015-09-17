---
layout: post
title: New Silverlight 4 Service Release 4.0.50826.0
date: 2010-09-01 13:59
author: John
comments: true
categories: [Silverlight]
---
<p>Today we released a new update to for Silverlight 4 (4.0.50826.0) and a new SDK to go along with it.&#160; <a href="http://timheuer.com/blog/archive/2010/09/01/silverlight-service-release-september-2010-gdr1.aspx">Tim Heuer posted a summary here</a> and you can <a href="http://support.microsoft.com/kb/2164913">check out the full details at KB2164913</a>. I summarized the key elements below.</p>  <p>Here are the relevant highlights:</p>  <ul>   <li>SDK feature to enable Add New Row capabilities in DataGrid control </li>    <li>Improving startup performance of Silverlight applications </li>    <li>Adding mouse wheel support for out-of-browser applications on the Mac platform </li>    <li>Various media-related fixes around DRM content </li>    <li>Fixed memory leak when MouseCapture is used </li>    <li>Fixed memory leak for DataTemplate usage</li> </ul>  <p><strong>For Users</strong></p>  <p>Tim aptly points out that if you want to encourage your end users to upgrade to this new Silverlight version then you will want to set the minRuntimeVersion parameter in the object tag hosting your Silverlight control to 4.0.50826.0. You’ll also want to set autoUpgrade to true.</p>  <div style="border-bottom: silver 1px solid; text-align: left; border-left: silver 1px solid; padding-bottom: 4px; line-height: 12pt; background-color: #f4f4f4; margin: 20px 0px 10px; padding-left: 4px; width: 97.5%; padding-right: 4px; font-family: &#39;Courier New&#39;, courier, monospace; direction: ltr; max-height: 200px; font-size: 8pt; overflow: auto; border-top: silver 1px solid; cursor: text; border-right: silver 1px solid; padding-top: 4px" id="codeSnippetWrapper">   <pre style="border-bottom-style: none; text-align: left; padding-bottom: 0px; line-height: 12pt; border-right-style: none; background-color: #f4f4f4; margin: 0em; padding-left: 0px; width: 100%; padding-right: 0px; font-family: &#39;Courier New&#39;, courier, monospace; direction: ltr; border-top-style: none; color: black; font-size: 8pt; border-left-style: none; overflow: visible; padding-top: 0px" id="codeSnippet">...<br />...<br />&lt;<span style="color: #008000">;param name=&quot;minRuntimeVersion&quot; value=&quot;4.0.50826.0&quot; /&gt;</span><br />&lt;<span style="color: #008000">;param name=&quot;autoUpgrade&quot; value=&quot;true&quot; /&gt;</span><br />...<br />...<br /></pre>
<br /></div>
<p><strong>For Developers</strong></p>
<p>For Silverlight developers you will want to grab the new developer bits and updated SDK:</p>
<ul>
<li><a href="http://go.microsoft.com/fwlink/?LinkID=188039">Windows <strong>developer</strong> runtime</a></li>
<li><a href="http://go.microsoft.com/fwlink/?LinkID=188040">Mac <strong>developer</strong> runtime</a></li>
<li><a href="http://go.microsoft.com/fwlink/?LinkID=188043">Silverlight 4.0.50826.0 SDK</a></li>
</ul>
<p>Enjoy!</p>

