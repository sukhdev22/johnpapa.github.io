---
layout: post
title: Invalid References in Entity Framework
date: 2008-01-30 15:10
author: John
comments: true
categories: [All]
---
<p>We all make mistakes ... I know I certainly do. Today I made one that only set me back about 10 minutes ... but I admit I felt silly after I realized what I did wrong. Today I created a new VS 2008 project, added an Entity Data model (aka EDMX file) to the project, and began setting up my EDM. When i went to build the project I received a ton of errors about invalid references. So I checked my references folder and bam! ... several dll's were marked is invalid.</p> <p><a href="/wp-content/uploads/files/media/image/WindowsLiveWriter/InvalidReferencesinEntityFramework_D557/image_6.png"><img style="border-right: 0px; border-top: 0px; border-left: 0px; border-bottom: 0px" height="244" alt="image" src="/wp-content/uploads/files/media/image/WindowsLiveWriter/InvalidReferencesinEntityFramework_D557/image_thumb_2.png" width="214" border="0"></a> </p> <p>The quick and easy solution to this problem was that I forgot to set the target framework of my project to .NET Framework 3.5. </p> <p><a href="/wp-content/uploads/files/media/image/WindowsLiveWriter/InvalidReferencesinEntityFramework_D557/image_8.png"><img style="border-right: 0px; border-top: 0px; border-left: 0px; border-bottom: 0px" height="137" alt="image" src="/wp-content/uploads/files/media/image/WindowsLiveWriter/InvalidReferencesinEntityFramework_D557/image_thumb_3.png" width="244" border="0"></a> </p> <p>Once this is done everything is happy as Ferris Bueller in a parade. </p>

