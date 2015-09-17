---
layout: post
title: How to use npm global without sudo on OSX
date: 2014-12-28 01:24
author: John
comments: true
categories: [node, npm, osx, sudo, Uncategorized]
---
When running npm and node, you may find yourself getting permission errors that ultimately lead you to using <code>sudo</code> in your commands. While this helps get around the issue in the short-term, it also places stricter permissions on those installs and it becomes a slippery slope where soon you may need sudo for more than you bargained for. Also, do you really want to be using <code>sudo</code> to install npm packages?

I went down this path and some experienced Mac developers helped me see why I needed to relieve myself of <code>sudo</code> for npm. Since then I've read several great posts with directions on how to do this including <a href="https://gist.github.com/DanHerbert/9520689">Dan Herbert's fixing npm for Homebrew users</a> and <a href="https://github.com/sindresorhus/guides/blob/master/npm-global-without-sudo.md">Sindre Sorhus's No Sudo instructions</a>. Each of these has something to offer, of which I combined into a single set of steps in this post. Also, special thanks to <a href="https://twitter.com/briannoyes">Brian Noyes</a>, <a href="https://twitter.com/wardbell">Ward Bell</a>, <a href="https://twitter.com/jesterxl">Jesse Warden</a>, <a href="https://twitter.com/walkingriver">Mike Callaghan</a>, and <a href="https://twitter.com/SamArtioli">Sam Artioli</a> for their help.

Some people already have node and npm packages. So there is some cleanup to do first. Others have fresh machines, so it's a bit easier. While these steps are not the only way to go, they have been repeatable on a few machines for me. So why create a new set of instructions? For one, I can add some additional comments of what is going on to try to explain what's really happening. Also, I was able to take some of the steps and make them all run from terminal, so you can literally copy and paste some of them (see where this is recommended below).

<blockquote>
  Disclaimer: I offer no warranty nor guarantee of the success of these steps. These are simply what works in my experience. Follow these steps with a cautious eye as you would any steps you find on the internet.
</blockquote>

I also encourage you to refer to either of the posts I mention above as they are both excellent and have also worked for me.

<h2>What Are We Really Doing?</h2>

Good question!  When node installs it puts npm packages in a specific folder, usually <code>/usr/local/lib/node_modules</code>. This location is what we are moving in these steps. Why? Because that location requires root permissions and thus the use of sudo proliferates needlessly. So these steps are all about moving the location of where the npm packages will live, and then pointing OSX and node to the new location via paths. Think of it as moving to a newer neighborhood :)

<h2>Homebrew</h2>

I assume you have <a href="http://brew.sh/">Homebrew</a>. If not, go get it. It's awesome for OSX. You can install tons of great stuff quickly and efficiently with it. Instructions are at the link or for your convenience, run this:

<code>ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"</code>

<h2>Already Have Node ?</h2>

If you have Node installed already via brew, remove it and npm first. Run step 1 by itself and be careful, we are running as sudo and we are removing files forcefully.

<ul>
<li>This removes, forcefully, everything in the old npm folders. 
<code>sudo rm -rf /usr/local/lib/node_modules</code>
<code>sudo rm -rf ~/.npm</code></p></li>
<li><p>This removes node and puts it back without npm
<code>brew uninstall node</code></p></li>
</ul>

<h2>Install Node and NPM</h2>

<ol>
<li><p>This adds node, sans npm
<code>brew install node --without-npm</code></p></li>
<li><p>Create a directory for your global packages. I prefer to name my folder <code>.npm-packages</code>, you can choose what you want as long as you replace it throughout these steps. The ${HOME} is a variable that translates to <code>~/</code> or <code>/Users/john/</code> for me.
<code>mkdir "${HOME}/.npm-packages"</code></p></li>
<li><p>Reference this directory for future usage in your <code>.bashrc</code> file. The <code>echo</code> command helps write the statement. The <code>&gt;&gt;</code> tells it where to write it which is followed by the file to write it to.
<code>echo NPM_PACKAGES="${HOME}/.npm-packages" &gt;&gt; ${HOME}/.bashrc</code></p></li>
<li><p>Indicate to npm where to store your globally installed package, in your <code>~/.npmrc</code> file.
<code>echo prefix=${HOME}/.npm-packages &gt;&gt; ${HOME}/.npmrc</code></p></li>
<li><p>This gets and installs the latest npm, which is 2.1.16 at the time of this writing.
<code>curl -L https://www.npmjs.org/install.sh | sh</code></p></li>
<li><p>Ensure node will find the packages by adding the path to your <code>.bashrc</code>. Notice the escape characters before special characters.
<code>echo NODE_PATH=\"\$NPM_PACKAGES/lib/node_modules\:\$NODE_PATH\" &gt;&gt; ${HOME}/.bashrc</code></p></li>
<li><p>Ensure you'll find installed binaries by adding the following to your <code>.bashrc</code>.
<code>echo PATH=\"\$NPM_PACKAGES/bin\:\$PATH\" &gt;&gt; ${HOME}/.bashrc</code></p></li>
<li><p>Ensure that you source your <code>.bashrc</code> file by adding the following to your <code>.bash_profile</code>.
<code>echo source "~/.bashrc" &gt;&gt; ${HOME}/.bash_profile</code></p></li>
<li><p>Source your <code>.bashrc</code> file once. Previous step did this for the future, but this does it right away.
<code>source ~/.bashrc</code></p></li>
</ol>

<blockquote>
  <p>These <code>echo</code> commands will create the file if it is not already there. But if the file is there, it will simply append these commands to the end of the file. If you already had these it will add a duplicate, which you then should remove. See the section below for details.
</blockquote>

<h2>Checking Your Files</h2>

When you are done, you should have a files that looks something like the following:

<ul>
<li><code>~/.npmrc</code></li>
</ul>

<pre><code>prefix=/Users/john/.npm-packages
</code></pre>

<ul>
<li><code>~/.bashrc</code></li>
</ul>

<pre><code>NPM_PACKAGES=/Users/john/.npm-packages
NODE_PATH="$NPM_PACKAGES/lib/node_modules:$NODE_PATH"
PATH="$NPM_PACKAGES/bin:$PATH"
</code></pre>

<ul>
<li><code>~/.bash_profile</code></li>
</ul>

Make sure you have the <code>source ~/.bashrc</code> in your <code>~/.bash_profile</code>

<blockquote>
  <blockquote>
    To see the files beginning with <code>.</code> such as <code>.bashrc</code> and <code>.npmrc</code> you need to show hidden files for OSX. In terminal run the following command: <code>defaults write com.apple.finder AppleShowAllFiles YES</code>
  </blockquote>
</blockquote>

<h2>Verification</h2>

Run these commands to test if you were successful:

<ul>
<li>Run <code>node -v</code> to see the version of node</li>
<li>Run <code>npm -v</code> to see the version of npm</li>
<li>Run <code>npm list -g --depth=0</code> to see the global npm packages you have installed (should just be npm right now)</li>
</ul>

<h2>Advanced Users</h2>

For advanced users, the rest of these can be run via copy and paste into terminal.

<code class="prettyprint">
brew install node --without-npm
mkdir "${HOME}/.npm-packages"
echo NPM_PACKAGES="${HOME}/.npm-packages" >> ${HOME}/.bashrc
echo prefix=${HOME}/.npm-packages >> ${HOME}/.npmrc
curl -L https://www.npmjs.org/install.sh | sh
echo NODE_PATH=\"\$NPM_PACKAGES/lib/node_modules&#58;\$NODE_PATH\" >> ${HOME}/.bashrc
echo PATH=\"\$NPM_PACKAGES/bin&#58;\$PATH\" >> ${HOME}/.bashrc
echo source "~/.bashrc" >> ${HOME}/.bash_profile
source ~/.bashrc
</code>
