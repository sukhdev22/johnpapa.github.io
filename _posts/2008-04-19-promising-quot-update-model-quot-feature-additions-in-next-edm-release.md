---
layout: post
title: Promising "Update Model" Feature Additions in Next EDM Release
date: 2008-04-19 02:26
author: John
comments: true
categories: [All]
---
<p>If you have tried the "Update Model from Database" feature in the Entity Framework's EDM tool (latest version is the EDM CTP 2) you probably have noticed that it currently does not fully update the DB model as well as you hoped. I know I got excited when I first saw the feature, but quickly had a let down as I knew I had to wait til the next release to get more out of this feature. This month <a href="http://blogs.msdn.com/adonet/archive/2008/04/01/update-model-from-db.aspx">Noam Ben-Ami gave us a preview of some of the new features that will be in the next release of the EDM</a>. You definitely want to check this out.</p> <p>I am thrilled to see that the Update Model from Database feature will not remove items from the conceptual model. Though instead of simply showing errors, I would not mind it asking me with some type of wizard that prompts me with suggestions. For example, when a column has been removed from a table in the database it would be awesome if a list of issues was presented and along with options to take action (such as remove property from the entity and refactor). yeah, yeah, I know its being picky :) </p> <p>I also love how its smart enough to detect that a hierarchical relationship in the conceptual model may represent multiple tables in the the database.&nbsp; Its getting much closer!!!</p>

