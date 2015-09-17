---
layout: post
title: Durandal, Breeze and Ruby
date: 2013-09-04 02:26
author: John
comments: true
categories: [breeze, javascript, ruby on rails, SPA, Uncategorized]
---
Have you been itching to see a SPA using <a href="http://www.durandaljs.com" target="_blank">Durandal</a> and <a href="http://www.breezejs.com" target="_blank">Breeze</a> without entity Framework on the back end? The inventors of Breeze have answered that call by taking the <a href="http://jpapa.me/spajsps" target="_blank">Code Camper SPA using Durandal and Breeze from my Pluralsight course</a> and swapped out the entire back end so it is now using Ruby on Rails. This is huge as it demonstrates how you can use Breeze in a SPA without relying strictly on the metadata tat Entity Framework (EF) provides. Sure EF makes it darn easy, but it is not the only game in town. 

Check out this <a href="http://www.breezejs.com/samples/intro-spa-ruby" target="_blank">article about the Ruby/Durandal/Breeze demo</a> to see it in action and learn more about how the Breeze folks wrote it. <a href="https://github.com/IdeaBlade/Breeze/tree/master/Samples/CCJS-Ruby" target="_blank">Download the CCJS-Ruby source code</a> and run the app yourself.

<a href="http://www.breezejs.com/samples/intro-spa-ruby" target="_blank"><img src="http://www.breezejs.com//sites/all/images/ruby/sessions.png" width="610" height="745" class="alignleft" /></a>

There is a quick run-down from their site on what they changed from ASP.NET and EF to Ruby. Obviously the back end changed to fit a more natural Ruby feel. The front end changed a little bit to add a Breeze-AJAX request interceptor an an Active Record data service adapter.

I enjoy working with ASP.NET, ASP.NET Web API and Entity Framework among other Microsoft stalwarts. But it's nice to see practically the same SPA client code with Durandal and Breeze working with  a Ruby back-end. Special kudos to <a href="http://twitter.com/wardbell" target="_blank">Ward Bell</a> for working so hard on this!
