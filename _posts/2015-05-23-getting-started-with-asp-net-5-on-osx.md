---
layout: post
title: Getting Started with ASP.NET 5 on OSX
date: 2015-05-23 18:03
author: John
comments: true
categories: [Uncategorized]
---
ASP.NET 5 is something special. We can build cross platform Web apps using .NET Core that run on OSX, Linux and Windows. But how do you get started on OSX? This post shows how quickly you can get up and running.

<blockquote>
  Dan Wahlin, Ward Bell and I are hosting an ASP.NET 5 workshop at <a href="https://anglebrackets.org/">DevIntersections / Anglebrackets in Las Vegas</a> in Novemxber. Use promo code PAPA to get $50 off the event and come visit us. Registration will open in early June.
</blockquote>

Here are some commands you should get familiar with:

<ul>
<li><strong>dnvm</strong> is the .NET version manager. You'll run this occasionally to update your versions</p></li>
<li><p><strong>dnu</strong> is the .NET package updater. This can update nuget packages and can also help update npm and bower packages via <code>project.json</code>.</p></li>
<li><p><strong>dnx</strong> is the .NET execution runtime. You'll use this to run your app</p></li>
</ul>

<h2>Installation</h2>

<p>First, start with getting the tools you need so you can run ASP.NET. The first step is to install homebrew, which is like Walmart for OSX. Homebrew makes it easy to download and install ton of great software libraries and tools. We'll use this to install and setup ASP.NET.

<ol>
<li>Install <a href="http://brew.sh/">homebrew</a> by entering this at a terminal

<pre><code class="bash">ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
</code></pre></li>
<li>Use homebrew to get ASP.NET

<pre><code class="bash">brew tap aspnet/dnx
brew update
</code></pre></li>
<li>Add the following to the <code>~/.bash_profile</code> or <code>~/.bashrc</code> file. This makes it easy to use dnvm.

<pre><code class="bash">source dnvm.sh
</code></pre></li>
<li>Use homebrew to get the .NET version manager (dnvm) and upgrade the dnvm to the latest version

<pre><code class="bash">brew install dnvm
dnvm upgrade
</code></pre></li>
</ol>

And now you have ASP.NET 5!

<h2>File New Project</h2>

Creating a new project is easy with Yeoman. This is my preferred way to scaffold new projects on Mac or Windows. No more file new for me in the IDE!

There is a generator that the ASP.NET team helps curate named <a href="https://github.com/OmniSharp/generator-aspnet">generator-aspnet</a>. This is a good starting place, though I and many others will also be creating generators too.

<ol>
<li>Install yo and gulp. You will use yo to run the generator and gulp to help automate tasks.

<pre><code>npm install -g yo gulp
npm install -g generator-aspnet
</code></pre></li>
<li>Install the ASP.NET generator and run it with the gulp option. This generators a project using gulp, instead of grunt.

<pre><code>yo aspnet --gulp
</code></pre></li>
<li>Choose your project type. Web API Application, Empty Web, Console, or MVC Web App.</p></li>
<li><p>run the app

<pre><code class="bash">dnx . kestrel
</code></pre></li>
</ol>

When you modify the packages list in <code>project.json</code> you should run <code>dnu restore</code> to get the latest ones.

Enjoy!
