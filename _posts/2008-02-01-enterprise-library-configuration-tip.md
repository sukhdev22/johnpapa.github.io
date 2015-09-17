---
layout: post
title: Enterprise Library Configuration Tip
date: 2008-02-01 18:51
author: John
comments: true
categories: [All]
---
<p>This is a simple error with a simple solution, one which I run into every once in a while since I am always moving projects around on my computer. Just in case you run into it, here its the issue:</p> <p><strong><em>Situation</em></strong>:</p> <ul> <li>Enterprise Library 1.1</li> <li>Using Configuration Tool</li> <li>.NET Project has been moved from one folder to another</li> <li>Using the Encryption Settings to encrypt the config</li></ul> <p><strong><em>Symptoms</em></strong>:</p> <ul> <li>When opening the Enterprise Library 1.1 Configuration Tool&nbsp;and opening the app.config (or web.config) of a project, you receive the error:</li> <li>Could not find part of the path: &ldquo;c:\somewhere on your computer\mycrypto.key&rdquo;</li></ul> <p><strong><em>&nbsp;The Problem:</em></strong></p> <ul> <li>The app.config file is still pointing to the original location of the crypto key file. </li> <li>However, you can&rsquo;t change the location in the app.config file using the Ent Lib Configuration tool because of this error. Don;t you just love circular issues?</li></ul> <p><strong><em>&nbsp;The Solution:</em></strong></p> <ul> <li>&lt;grin&gt; Don&rsquo;t move your projects on your computer &lt;/grin&gt;</li> <li>No, seriously &hellip;all you have to do is edit the app.config file manually in some text or xml editor of your choice and re-point it to the correct crypto key file location. Once you do that, you can open and edit your project in the Enterprise Library Configuration tool just fine.</li></ul> <p>&nbsp;</p>

