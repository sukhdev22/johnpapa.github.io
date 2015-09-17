---
layout: post
title: Automatically Restarting ASP.NET on OSX with DNXMON
date: 2015-05-23 18:15
author: John
comments: true
categories: [Uncategorized]
---
Write some code, see it run, refactor the code, see it run, refactor ... you get the idea. This is what I do all day long. Notice I didn't say "write code, refactor, stop server, start server, write code ...". Why? Because I prefer my server to detect the code changes and auto-restart. This works great in Node.js with nodemon, so this post shows one option to do that for ASP.NET on OSX.

<blockquote>
  Learn how to <a href="http://www.johnpapa.net/getting-started-with-asp-net-5-on-osx/">get started with ASP.NET 5 on OSX here</a>
  Add this script to your <code>~/.bash_profile</code>. Then when you type <code>dnxmon . kestrel</code> your ASP.NET app will start and watch the cs and json files. When they change, dnx will restart.
</blockquote>

I expect something more elegant to come in time from the ASP.NET team (there is a kmon in the works, using the old name of dnx). But for now, this makes it easy to speed up my development process.

<h3>dnxmon</h3>

Run dnx server continuously with nodemon watching for changes to cs or json files

<pre><code class="bash">dnxmon() {
    # Run dnx server continuously with nodemon 
    # watching for changes to cs or json files
    # Usage:
    #   dnxmon &lt;directory&gt; &lt;command&gt;
    # dnxmon (applies the defaults: current directory and the "web" command)

    dnxmonFn() {
        nodemon --ext "cs,json" --exec "dnx $1 $2"
    }

    if [[ $# -eq 0 ]]
    then
        echo "running default ..."
        echo "nodemon --ext "cs,json" --exec "dnx . kestrel""
        dnxmonFn . kestrel
    else
        if [[ $# -eq 2 ]]
        then
            echo "nodemon --ext "cs,json" --exec "dnx $1 $2""
            dnxmonFn $1 $2
        else
            echo "must supply directory and command,"
            echo "such as dnxmon . kestrel"
        fi
    fi
}
</code></pre>
