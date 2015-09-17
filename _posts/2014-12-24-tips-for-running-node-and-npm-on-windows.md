---
layout: post
title: Tips for Running Node and NPM on Windows
date: 2014-12-24 16:40
author: John
comments: true
categories: [chocolatey, node, npm, python, Uncategorized, visual studio, windows]
---
I recently helped a few folks get node and npm up and running on Windows. Here are some of the steps we were able to follow to make this all work.

<h2>Requirements</h2>

The systems already had the latest version of <a href="http://www.visualstudio.com/news/vs2015-preview-vs">Visual Studio 2015 Preview</a> or the free <a href="http://www.visualstudio.com/en-us/news/vs2013-community-vs.aspx">Visual Studio Community</a> edition. I highly encourage starting there. Also, make sure git is install.

<ul>
<li>Latest version of Visual Studio</li>
<li>git</li>
<li><a href="https://chocolatey.org/">Chocolatey</a></li>
</ul>

<h2>Running Node and NPM on Windows</h2>

First get node via chocolatey. You may have to update your paths. Sometimes paths were updated for us, sometimes they were not. Your mileage may vary.

Run these from an administrator command prompt or console2 or whatever your favorite terminal is.

<code>choco install nodejs</code>
<code>choco install nodejs.install</code>

Now install an older version of python. Had lots of issues with the latest python, so this one seemed to work.

<code>choco install python -version 2.7.2</code>

You also may want to upgrade npm on Windows. You can <a href="https://github.com/npm/npm/wiki/Troubleshooting#upgrading-on-windows">upgrade npm by following these instructions</a>
