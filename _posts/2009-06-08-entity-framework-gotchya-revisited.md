---
layout: post
title: Entity Framework Gotchya Revisited
date: 2009-06-08 19:38
author: John
comments: true
categories: [All]
---
<p>This is not the first time I have hit this issue, and it has been documented by people like Julie Lerman … but for my own sake I decided to blog about it in case I hit it again. It seems like I run into this issue just about the time I forget how to resolve it :)</p>  <p>The problem sometimes occurs with the Entity Framework where it gives an array of errors when doing simple operations. For example, I received an error about not being able to “unable to load the specified metadata resource”. Uh, the connection string information is right in the config file! The problem often can be resolved simply by:</p>  <ol>   <li>open the EDMX file in the designer mode </li>    <li>go to the properties of the EDMX </li>    <li>set the Metadata Artifact Processing property to “Copy to Output” </li>    <li>build the project </li>    <li>go back and change the property to the appropriate setting of “Embed in Output Assembly” </li> </ol>  <p>I’ve only hit this a few times but when i get this error, this has always resolved the problem for me.</p>

