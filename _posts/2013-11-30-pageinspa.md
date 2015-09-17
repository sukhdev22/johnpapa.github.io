---
layout: post
title: SPA and the Single Page Myth
date: 2013-11-30 19:58
author: John
comments: true
categories: [angular, durandal, ember, SPA, Uncategorized]
---
SPA is one of the most exciting technology strategies today, but it may be one of the worst terms in modern web development. Just the word "Page" can have many meanings.
<h3>SPA Misconceptions</h3>
Chances are you have heard the term SPA tossed around at the office. SPA's are on the rise but there are a lot of misconceptions about what SPA means. SPA stands for Single Page Applications ... but are they truly a Single Page App? I've found that one of the biggest hurdles for folks understanding SPA is the term itself. The name can often imply that you are building a single page, with a single set of functionality, such as a search screen or a To-Do list app. 
<img src="http://www.johnpapa.net/wp-content/uploads/2013/11/catspa-300x224.jpg" alt="catspa" width="300" height="224" class="alignleft size-medium wp-image-22461" /> 

Now let's play out a common scenario where you are a developer and you are making your case for the architecture of your new project to your manager, Bob. You ask for Bob's permission to build the next mission critical app on a Single Page App strategy. Bob knows the user will see dozens of pages, so Bob might suspect you and the development team that you might be looking for an excuse to use the "latest and greatest" and that it won't work for multiple pages. "We need more than 1 page" Bob says. We developers tend to gravitate to the shiny new objects. But I don't think we can blame Bob in this case as the term SPA can easily be misconstrued. You and I both know a SPA is much more than a "single" page, right? Or is it? The answer to that lies in your interpretation of what a "page" is, and that is why I wrote this post :)

Let me be clear: you can build a SPA that supports robust business applications. <a href="http://angularjs.org" target="_blank">Angular</a>, <a href="http://durandaljs.com" target="_blank">Durandal</a>, and <a href="http://emberjs.com/" target="_blank">Ember</a> are three great SPA presentation frameworks that lead the way in this area. So how do we break down this barrier and get the point across that a SPA can fully support large-scale application development? It all starts with understanding the P in SPA. Ask a few developers what a "Page" is, you likely will get a variety of answers. So again, how can we blame Bob for misunderstanding its meaning? 

<h3>What's a Page?</h3>
One interpretation of what a page could mean is the "totality of whatever occupies the four walls of the application UI" (a quote from Ward Bell). If that content changes, then we've changed to a new "page". For example, a page switch could be what we do when we switch from Sessions to Speakers in this <a href="http://jpapa.me/cc-ng-z" target="_blank">live demo</a>. That's a fairly reasonable assumption, but that is not the "page" in a SPA.  

The "page" in SPA is the single web page that the server sends to the browser when the application starts. It's the server rendered HTML that gets everything started. No more, no less. After that initial page load, all of the presentation logic is on the client.

My friend <a href="https://twitter.com/wardbell" target="_blank">Ward Bell</a> defines the server and client roles perfectly here:
<blockquote>The server plays no part in determining what the application does with a SPA. That's the client's job. It's the client that composes application pages out of HTML templates (HTML fragments) and data, both of which it downloads on-demand asynchronously as it needs them.
</blockquote>

The server's diminished role is an important distinction in a SPA. The server has no UI logic. The server maintains no UI state. The server, however, does provide resources to the client. Those resources start out with the initial HTML for the web page (the shell) and may in response to client HTTP requests for data in the form of HTML fragments, JSON data, or on-demand JavaScript/CSS.

<h3>So Why is it Called Single?</h3>
The single page is the starting point. It's the first part of the app that gets the ball rolling. When a SPA starts, the first visible thing we notice is the initial server rendering of the shell. That shell is our single page. In many SPA's we won't ask for another complete page rendering again. We already have what we need in that initial page rendering and now we rely on the SPA presentation framework to help us orchestrate the HTML changes for the user within the confines of that single initial page. 

This is really important. In a SPA, we make one round trip to the server, up front, and get the initial HTML page.

<h3>HTML Fragments are Views</h3>
Let's revisit our conversation with Bob. You've explained to him that the Single Page in SPA is truly just a term that means the first page is rendered from the server, then the client takes over. Bob starts warming up when he hears you say that it's really a rich web app that can run on any platform, on a variety of devices, and in a modern browser. But Bob is smart, he wants to know how this single page will support the 2 dozen screens your app needs. Bob says "Once we get that initial page loaded, we need other pages, don't we?" This is where you introduce the term Views.

Views are the "other pages". The Views are HTML fragments that make up what the users commonly call screens or pages. A user might say "Go to the order entry screen" or "Go to the customer search page". Their terminology is different from developers, and that's OK as long as we understand how to translate it when we need to. In our developer speak the term "page" is overloaded. In a SPA everything the users sees is a "view". When a view occupies the entire screen we call that a page to reflect the fact that it visually commands the user's full attention. Technically, it's just a another view composed by the client.

We typically have many views in a SPA. Going back to the <a href="http://jpapa.me/cc-ng-z" target="_blank">live demo</a> you'll see there are several views. We can flip between speakers, sessions, attendees, speaker details and session details. These views, as we call them, are the answer to Bob's question. Yes we need other pages. SPA supports that well, we just call them views. That's an important distinction because we can have more than 1 view visible on the screen at one time.

SPA also supports more than 1 view on the screen at the same time. In the <a href="http://jpapa.me/cc-ng-z" target="_blank">live demo</a> the top navigation and the sidebar are also views. In a dashboard, we can load multiple views, too. So the term views really means an HTML fragment that offers a distinct set of functionality to the application. It often means the view follows the <a href="http://en.wikipedia.org/wiki/Single_responsibility_principle" target="_blank">Single Responsibility Principle</a> where the view can operate on its own in a variety of contexts. 

<h3>What's the Shell?</h3>
I've tossed around the term "shell" without properly introducing it, so let me correct that now. The shell is the layout and structure of your app. The visual parts that rarely change. The shell is generally loaded on the initial page load from the server and serves as the placeholder for all of your views. In the live demo, the shell is what contains the sidebar, the top navigation area, and the content area.

<h3>Navigation and Menus</h3>
Bob now understands the role of views and wants to know how you intend to allow the user to go between the views. Your app will have menus and navigation, so how does a SPA support that? This is where you explain routing. 

Most modern SPA presentation frameworks support the concept of routing via a service known as the router. The router's job is to allow the user to go from View A to View B within the browser by clicking some menu item. if you want to get all technical you can tell Bob about HTML5 push state and the browser's history and navigation stacks, but it's probably a more effective route to take (pun intended) to say that the app will have menus, it will support the browsers back and forward buttons, and it will allow a user to go to a specific place (view) in the app given a url (a term known as deep linking) without posting to the server.

When a user clicks on a menu item, the SPA sees that url and translates it to a View that should be displayed. If the view has not been seen before, the application may make an HTTP request to retrieve the HTML template for the view. Then it will compose the view, fill in the template, and display the view in the appropriate location within the shell. If the view has already been viewed once, the browser may have cached it and the router will be smart enough not to make the request. This is one way a SPA can reduce round-tripping to and from a server, and thus improve performance.

<h3>What is Data?</h3>
Another sticking point with SPA's is how the term data gets tossed around. A SPA requests data over HTTP from a server. Data is not simply a list of customers. Data can be JSON, HTML, or some other resource that the app requires. A SPA can be built to request these resources asynchronously and on-demand. As my friend <a href="http://jesseliberty.com" target="_blank">Jesse Liberty</a> observed:

<blockquote>... there is a big difference in my mind between saying "what is sent from the server to the client may include JavaScript, CSS or even HTML" on the one hand and "only data is sent from the server".</blockquote>

He has a great point. When we think of data, and more importantly when Bob thinks of data, he is likely thinking of the customers and orders in the app. And he is right, but data is not limited to the pure data in a SPA. The data can be anything the SPA client needs from the server. So perhaps this data term is overloaded and we should instead clarify this by saying that a SPA will request resources on-demand (or cache them if so desired) and those resources may be JSON data, HTML fragments, JavaScript or CSS. At least then Bob would clearly know we mean so much more than pure data.

So to clear this up let's stop calling it data and instead refer to it as resources. A SPA makes requests for resources from the server.

<h3>Worst Name Ever?</h3>
Well, I don't believe in total absolutes. But while SPA may not be the worst name ever it certainly is not the most clear term to describe them. In fact, I prefer to call them Rich Web Apps but RWA just sounds awful so I'll stick with SPA :)

PS - Special thanks to Ward Bell and Jesse Liberty for providing their feedback on this post, and for correcting my poor grammar.
