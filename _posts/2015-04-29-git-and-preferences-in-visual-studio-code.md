---
layout: post
title: Git and Preferences in Visual Studio Code
date: 2015-04-29 18:34
author: John
comments: true
categories: [Uncategorized]
---
Visual Studio Code has a good symbiosis with allowing you to customize the editor through styling, preferences, keyboard mappings, tasks, and more. Here are some examples of how to get started.

<h2>Visual Studio Code Series</h2>

Follow this series to learn more about what you can do with Visual Studio Code!

<ol>
<li><a href="http://johnpapa.net/visual-studio-code">Introducing Visual Studio Code</a></li>
<li><a href="http://johnpapa.net/getting-started-with-visual-studio-code">Getting Started with Visual Studio Code</a></li>
<li><a href="http://johnpapa.net/intellisense-witha-visual-studio-code">Intellisense</a></li>
<li><a href="http://johnpapa.net/refactoring-with-visual-studio-code">Refactoring</a></li>
<li><a href="http://johnpapa.net/debugging-with-visual-studio-code">Debugging</a></li>
<li><a href="http://johnpapa.net/git-and-preferences-in-visual-studio-code">Git Integration and Preferences</a></li>
</ol>

<h2>Git Integration</h2>

VSCode integrates well with git. When you make changes to your files you see red and green indicators in the left hand gutter of the editor. These markers show the changes you just made at those locations. Red indicates removed lines, green indicates added lines, and blue indicates changed lines.

<img src="http://www.johnpapa.net/wp-content/uploads/2015/04/git0.png" alt="git0" />

You can then click the git icon in the sidebar and see all of the changes. From here you can clean them (revert) one by one or as a group. You can also commit them all, add a commit message, and even push them right to the remote git repository.

<img src="http://www.johnpapa.net/wp-content/uploads/2015/04/git1.png" alt="git1" />

If you click on the file in the git view, VSCode will show you a side by side of the current state of the file as compared to its previous state.

<img src="http://www.johnpapa.net/wp-content/uploads/2015/04/git2.png" alt="git2" />

<h2>Preferences</h2>

You can adjust the setting sin VSCode by visiting the preferences and then overriding the default values with your own settings. You can access VSCode's preferences by either using the menu or via <code>CMD+,</code>.

<img src="http://www.johnpapa.net/wp-content/uploads/2015/04/preferencesmenu.png" alt="preferences menu" />

When you open preferences you open 2 files. The default settings (which are read only) and the <code>settings.json</code> file, where you can adjust your own preferences.

Simply add your settings to the object in the <code>settings.json</code> and VSCode will use those instead of the defaults. These are stored in the <code>.settings</code> folder. I like push this file in github with my source control.

<img src="http://www.johnpapa.net/wp-content/uploads/2015/04/preferences.png" alt="preferences" />

<h2>Styling</h2>

Light or dark theme? Zooming in? VSCode can do that too. I expect more to come when the rumored extensions are opened.

You can zoom in on the entire code window using <code>CMD++</code> or <code>CMD+-</code>, same as a browser.

You can swap between the light and dark themes from the menu <code>View</code> then <code>Theme</code> then <code>Light Theme</code> or <code>Dark Theme</code>.

<img src="http://www.johnpapa.net/wp-content/uploads/2015/04/theme-light.png" alt="theme-light" />

<img src="http://www.johnpapa.net/wp-content/uploads/2015/04/theme-dark.png" alt="theme-dark" />

<h2>Keyboard Mapping</h2>

You can override the keyboard mappings for VSCode, too. These are exposed in a <code>keyboard.json</code> file and can be accessed via the <code>Code</code> menu and then selecting <code>Preferences</code> and <code>Keyboard Shortcuts</code>.

<img src="http://www.johnpapa.net/wp-content/uploads/2015/04/keyboardmenu.png" alt="keyboard menu" />

You will see 2 files again: 1 for the default keybindings and 1 for the overrides (<code>keybindings.json</code>). Unmapped actions appear as comments at the bottom of the default list of key bindings.

<img src="http://www.johnpapa.net/wp-content/uploads/2015/04/keybindings.png" alt="keyboardbindings" />

While in the keybindings you will enjoy intellisense and auto completion.

Be sure not to set 2 key combinations to the same action.
