---
layout: post
title: Walking Through the Orchard Part 2 - Conversion from Graffiti
date: 2011-04-28 20:48
author: John
comments: true
categories: [Graffiti, Orchard, SQL CE, WebMatrix, WebPI]
---
<p>This is Part 2 of my series on setting up my blog for Orchard CMS. If you have not read Part 1, I suggest you go check it out first as it goes through the setup of the Orchard blog. In this post I will share what I went through to get converted out of Graffiti and to a format that Orchard can import (BlogML).</p>
<p><strong>The Series</strong></p>
<table width="400" cellpadding="1" cellspacing="1" border="0">
<tbody>
<tr>
<td width="400" valign="top"><a href="/orchardpart1">Walking Through the Orchard Part 1 &ndash; Setting up a Blog</a></td>
</tr>
<tr>
<td width="400" valign="top"><a href="/orchardpart2">Walking Through the Orchard Part 2 &ndash; Conversion from Graffiti</a></td>
</tr>
<tr>
<td width="400" valign="top"><a href="/orchardpart3">Walking Through the Orchard Part 3 &ndash; BlogML Import</a></td>
</tr>
<tr>
<td width="400" valign="top">Walking Through the Orchard Part 4 &ndash; ???</td>
</tr>
</tbody>
</table>
<h2>Where to Start?</h2>
<p>A few quick internet searches uncovered <a href="https://bitbucket.org/jonsagara/graffititoblogml/overview">a very useful program written by Jon Sagara (who says he converted it from VB to C# from Curt C)</a>. I downloaded it, unblocked it, extracted it, then added a few extra lines of code to write statements to the output window so I could watch the conversion as it went. I also changed the pointer to the database for Graffiti, so it could find the file to convert. Pretty easy change to the app.config file:</p>
<div id="codeSnippetWrapper" style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 20px 0px 10px; width: 97.5%; font-family: 'Courier New', courier, monospace; direction: ltr; max-height: 200px; font-size: 8pt; overflow: auto; cursor: text; border: silver 1px solid; padding: 4px;">
<div id="codeSnippet" style="text-align: left; line-height: 12pt; background-color: #f4f4f4; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">
<pre style="text-align: left; line-height: 12pt; background-color: white; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;"><span style="color: #0000ff;">&lt;</span><span style="color: #800000;">connectionStrings</span><span style="color: #0000ff;">&gt;</span></pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">    <span style="color: #0000ff;">&lt;</span><span style="color: #800000;">add</span> <span style="color: #ff0000;">name</span><span style="color: #0000ff;">="Graffiti"</span> <span style="color: #ff0000;">connectionString</span><span style="color: #0000ff;">="Data Source=C:\temp\Graffiti_JP.vdb3"</span><span style="color: #0000ff;">/&gt;</span></pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: white; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;"><span style="color: #0000ff;">&lt;/</span><span style="color: #800000;">connectionStrings</span><span style="color: #0000ff;">&gt;</span></pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">    </pre>
<!--CRLF--></div>
</div>
<p>Next I commented out the call to export to movable type and uncommented the call to export to BlogML (since that is what I use to import into Orchard). The lines of code I flipped are in the RunButton_Click handler in Form1.cs:</p>
<div id="codeSnippetWrapper" style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 20px 0px 10px; width: 97.5%; font-family: 'Courier New', courier, monospace; direction: ltr; max-height: 200px; font-size: 8pt; overflow: auto; cursor: text; border: silver 1px solid; padding: 4px;">
<div id="codeSnippet" style="text-align: left; line-height: 12pt; background-color: #f4f4f4; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">
<pre style="text-align: left; line-height: 12pt; background-color: white; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">ExportBlogML();</pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">//ExportMtImport();</pre>
<!--CRLF--></div>
</div>
<h2>Time to Run</h2>
<p>Overall it was a success. It took about 3 hours to run for about 630 posts and 3000+ comments, which is why I was glad I added the Console.Writeline statements so I could watch its progress. Total time from download of the program, initial tests and conversion was just under 5 hours. In the end I had a 4.5 MB XML file that I could use to import into Orchard once I was ready.</p>
<blockquote>
<p>NOTE: I ran this conversion for another blog which has about 40 posts and it took about 5 minutes. Not sure why the first one took so long &hellip; perhaps it was just an anomaly. The latter seems much more realistic. Maybe due to the comments I had &hellip; so basically, &ldquo;your mileage may vary&rdquo;.</p>
</blockquote>
<h2>Cleaning Up</h2>
<p>This conversion worked, but there were some things I wish I knew in advance that I did not find out until after I had already exported the content and then imported it into my Orchard instance. At that point, I just cleaned it up and moved on.</p>
<p>So went were those things? Well, the slugs were all exactly the same as the url&rsquo;s to the posts. I use slugs occasionally for posts like <a href="http://silverlight.tv">Silverlight TV</a> notices, so I knew I had to go fix these.</p>
<p>Next, the categories in Graffiti were exported as tags. If I looked closer at the BlogML I would have noticed this, but I didn&rsquo;t. So this was a casualty of my conversion that I was willing to live with and fix later.</p>
<p>The comments were all wrapped with a &lt;p&gt; and &lt;/p&gt; html tags. Easy fix once I got it into the destination database, but still annoying. Here is the TSQL I used to fix it.</p>
<blockquote>
<p>Caution: I am not responsible for what you do with this TSQL! So use at your own risk <img src="/wp-content/uploads/media/Windows-Live-Writer/Walking-Through-the-Orchard-Part-2--Conv_BE42/wlEmoticon-smile_2.png" alt="Smile" class="wlEmoticon wlEmoticon-smile" style="border-style: none;" />. In fact, I included a rollback transaction in here so you can try it and see the results before you commit it.</p>
</blockquote>
<div id="codeSnippetWrapper" style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 20px 0px 10px; width: 95.03%; font-family: 'Courier New', courier, monospace; direction: ltr; height: 210px; max-height: 200px; font-size: 8pt; overflow: auto; cursor: text; border: silver 1px solid; padding: 4px;">
<div id="codeSnippet" style="text-align: left; line-height: 12pt; background-color: #f4f4f4; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">
<pre style="text-align: left; line-height: 12pt; background-color: white; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;"><span style="color: #0000ff;">begin</span> <span style="color: #0000ff;">tran</span></pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">&nbsp;</pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: white; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;"><span style="color: #0000ff;">select</span> </pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">    Id,</pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: white; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">    CommentText, </pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">    <span style="color: #0000ff;">cast</span>(replace(replace(<span style="color: #0000ff;">cast</span>(CommentText <span style="color: #0000ff;">as</span> nvarchar(<span style="color: #0000ff;">max</span>)), <span style="color: #006080;">'&lt;p&gt;'</span>, <span style="color: #006080;">''</span>), <span style="color: #006080;">'&lt;/p&gt;'</span>, <span style="color: #006080;">''</span>) <span style="color: #0000ff;">as</span> ntext) <span style="color: #0000ff;">as</span> Expr1</pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: white; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;"><span style="color: #0000ff;">from</span> Orchard_Comments_CommentPartRecord</pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">&nbsp;</pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: white; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;"><span style="color: #0000ff;">update</span> Orchard_Comments_CommentPartRecord</pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;"><span style="color: #0000ff;">set</span>    CommentText = <span style="color: #0000ff;">cast</span>(replace(replace(<span style="color: #0000ff;">cast</span>(CommentText <span style="color: #0000ff;">as</span> nvarchar(<span style="color: #0000ff;">max</span>)), <span style="color: #006080;">'&lt;p&gt;'</span>, <span style="color: #006080;">''</span>), <span style="color: #006080;">'&lt;/p&gt;'</span>, <span style="color: #006080;">''</span>) <span style="color: #0000ff;">as</span> ntext) </pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: white; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">&nbsp;</pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;"><span style="color: #0000ff;">select</span> <span style="color: #cc6633;">@@rowcount</span></pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: white; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">&nbsp;</pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;"><span style="color: #0000ff;">select</span> </pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: white; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">    Id,</pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">    CommentText</pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: white; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;"><span style="color: #0000ff;">from</span> Orchard_Comments_CommentPartRecord</pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">&nbsp;</pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: white; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">&nbsp;</pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;"><span style="color: #0000ff;">rollback</span> <span style="color: #0000ff;">tran</span></pre>
<!--CRLF--></div>
</div>
<p>There may be other issues waiting for me, but this is what I found in the first few days.</p>
<p>So in summary, here are the issues I ran into:</p>
<ol>
<li>Slugs got hosed. Wish I knew in advanced, as I would have fixed the code. Hopefully my pain here is your gain. </li>
<li>Tags got hosed. Again, hindsight is 20/20. I have a SQL command I am working on to get these back, but its not bothering me that much. </li>
<li>Comments don&rsquo;t have names next to them. The user name (for the blog) was brought over for the comments when in fact I wanted the name the person entered in the comment. I don&rsquo;t require folks to log in, so my user names ere blank. In hindsight I would have brought over the Author name.&nbsp; You can fix this in the export code above. </li>
</ol>
<h2>Next Up</h2>
<p>The next part of&nbsp; this series will cover the import process into Orchard. And I am realizing that there will certainly be more parts to this series after that too as there is much more I have learned. Overall I am very happy with my decision to move to Orchard. The pains I have run into are almost entirely due to getting off of Graffiti.</p>
<p>I hope this helps! Please share your experiences too.</p>

