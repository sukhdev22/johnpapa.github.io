---
layout: post
title: Silverlight Consuming REST Services
date: 2008-05-16 16:44
author: John
comments: true
categories: [All]
---
<p>I just finished writing the first draft of a sample I am including in <a href="/all/as-it-once-was-i-am-writing-a-book/">my upcoming book tentatively titled Data Access with Silverlight 2 by O'Reilly</a>. Without giving too much away yet since the final details of the contract are not set in stone, the application example consumes a REST service, manipulates it through LINQ to XML, and binds it to various controls and some composite controls. The interaction with the <a href="http://en.wikipedia.org/wiki/Representational_State_Transfer">REST</a> (REpresentational State Transfer) services is pretty slick and quite easy when using Silverlight and LINQ to XML. Of course there are always issues to deal with, but overall it works very nicely.</p> <p>Why use REST? Well, REST services are becoming more abundant on the web. They do not expose a contract like WCF so when you deal with this type of data you can parse the XML using LINQ to XML or some other XML tools (though LINQ TO XML is so smooth why bother with anything else in this case). So this raw XML comes barreling into your Silverlight application asynchronously, LINQ to XML makes it fall in line, and its bound to where it needs to go via XAML.</p> <p>Sending data back via REST is also very cool. I've got that working now too. I have to be careful not to go overboard fine tuning the examples though or the book will never get written :) Interacting with REST from Silverlight applications is just one piece of the data access puzzle, but its pretty cool.</p> <p><img height="240" src="/wp-content/uploads/images/book2.png" width="183"></p>

