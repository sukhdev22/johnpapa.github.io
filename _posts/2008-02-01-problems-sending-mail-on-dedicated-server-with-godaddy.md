---
layout: post
title: Problems Sending Mail on Dedicated Server with GoDaddy
date: 2008-02-01 18:53
author: John
comments: true
categories: [All]
---
<div class="Section1"><p class="MsoNormal">I set up a new dedicated server at GoDaddy.com this weekend. One of the issues I struggled with was when I set up <a href="http://www.mailenable.com/download.asp">MailEnable</a> to run on the server I could not send mail. I could receive it just fine, but it would not go out anywhere. A friend of mine helped me track down what the issue was and it turns out that I could not connect to other sites through port 25. After digging through GoDaddy&rsquo;s support pages we found <a href="http://help.godaddy.com/article.php?article_id=122&amp;topic_id=120">a note about how GoDaddy blocks port 25</a> and that you have to use a Smart Host to send email through a relay server they set up. Of course this works, but it&rsquo;s a bit annoying that I bought a dedicated server and they are blocking me from sending out on port 25. </p><p class="MsoNormal">&nbsp;</p><p class="MsoNormal">So if you go buy a dedicated server from GoDaddy and you intend to set up you won mail server on it, be aware that you must use the smart host to send mail. So far everything else has been fine. The server looks good, its fast as I need it, and the price was great when compared to other hosting providers.</p></div>

