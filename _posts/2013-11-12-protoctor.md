---
layout: post
title: Setting the Prototype Constructor in JavaScript
date: 2013-11-12 15:20
author: John
comments: true
categories: [javascript, Prototype, Uncategorized]
---
While writing the upcoming Part 2 of <a href="http://jpapa.me/spangz" target="_blank">my Pluralsight course Building Apps with Angular and Breeze</a>, I found myself wanting to extend a constructor object with another constructor's members. I had an object called <code>AbstractRepository</code> that has a set of functions (ex: <code>getAll</code>, <code>queryFailed</code>) that could be shared by many repositories. I had a <code>LookupRepository</code> with its own functions that are very specific to getting "lookups". The way I settled on was to extend the <code>AbstractRepository</code>'s functions onto the <code>LookupRepository</code> by setting the prototype's constructor. The result is that the <code>LookupRepository</code> gets all the functions that it has plus the <code>AbstractRepository</code>'s functions too.

<blockquote>This technique is something <a href="http://twitter.com/wardbell" target="_blank">Ward Bell</a> and hashed out together during one of our code pairing sessions. It's great what you can achieve when you work together! We adapted this from some ideas from <a href="http://stackoverflow.com/questions/8453887/why-is-it-necessary-to-set-the-prototype-constructor" target="_blank">this answer in StackOverflow</a>.</blockquote>

First I create the constructor function for the <code>LookupRepository</code>.

<pre class="prettyprint linenums">
// LookupRepository
function Ctor(mgr) {
    this.repoName = 'repository.lookup';
    this.entityName = 'lookups';
    this.manager = mgr;
    // Exposed data access functions
    this.getAll = getAll;
    this.setLookups = setLookups;
}

AbstractRepository.extend(Ctor);

return Ctor;
</pre>

The <code>AbstractRepository</code> was injected into <code>LookupRepository</code> (using <a href="http://angularjs.org" target="_blank">Angular</a>'s dependency injection). Notice I extend it by calling a method on the <code>AbstractRepository</code> and passing in the constructor function for the <code>LookupRepository</code>. 
<pre class="prettyprint">
AbstractRepository.extend(Ctor);
</pre>

The <code>AbstractRepository</code>'s extend function set's the prototype for the <code>LookupRepository</code> to the <code>AbstractRepository</code>'s constructor function. This extends the <code>AbstractRepository</code>'s  functions to the <code>LookupRepository</code>. Then we make sure the <code>LookupRepository</code> gets back its constructor function. So now the <code>LookupRepository</code> will have the functions from both repositories.

<pre class="prettyprint linenums">
// AbstractRepository
function Ctor() { }

Ctor.extend = function (repoCtor) {
    // Allow this repo to have access to 
    // the Abstract Repo's functions,
    // then put its own Ctor back on itself.
    repoCtor.prototype = new Ctor();
    repoCtor.prototype.constructor = repoCtor;
};
</pre>

The <code>AbstractRepository</code>'s function are now accessible from the <code>LookupRepository</code>. So if the <code>AbstractRepository</code> has some generic functions like <code>_getAllLocal</code> which may get all of the data for a given resource, then <code>LookupRepository</code> can use it.  

<pre class="prettyprint linenums">
// AbstractRepository
Ctor.prototype._getAllLocal = _getAllLocal;
Ctor.prototype._queryFailed = _queryFailed;
</pre>

This adds value when you have a set of repositories such as <code>LookupRepository</code>, SessionRepository, SpeakerRepository, AttendeeRepository, and so on where they all can re-use the common functions from <code>AbstractRepository</code>.

I don't need this technique often, but it does come in handy. 


