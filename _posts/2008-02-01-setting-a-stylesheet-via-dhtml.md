---
layout: post
title: Setting a Stylesheet via DHTML
date: 2008-02-01 18:51
author: John
comments: true
categories: [All]
---
<P>Ever wanted to designate a style sheet via DHTML? Well, I hadn't needed to until recently. I have an application that reads an XML data island which tells the page the file name of the style sheet to use. (It could be any file of a hundred files, so I don;t want to load alternate style sheets in this case.) So here is the solution I decided on ...</P> <P>First ... I created a link tag with an empty href reference. The DOM doesn't store add an item to the document's stylesheet collection unless is has an href attribute.</P> <P><FONT color=#006400>&lt;link id="mainStyle" href="" type="text/css" rel="stylesheet"&gt;</FONT></P> <P>Next, I created some client side javascript that finds locates the mainStyle stylesheet reference and associates it to a specific URL where the stylesheet can be found.</P> <P><FONT color=#000080>&lt;script&gt;<BR>&lt;!--//<BR>&nbsp;&nbsp;&nbsp;document.styleSheets.item("mainStyle").addImport("../css/mystyles.css");&nbsp;&nbsp; <BR>//--&gt;<BR>&lt;/script&gt;</FONT><BR></P> <P>Of course, I don't hard code the path to the css file. Instead, I read the path from the XML data island and use that. Not much to it, but it does the job. :-)</P>

