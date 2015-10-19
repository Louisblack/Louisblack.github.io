---
title: 'Media Server &#8211; FreeNAS'
author: admin
layout: post
permalink: /2010/05/media-server-freenas/
categories:
  - Geek
  - Media Server
tags:
  - Apple
  - freenas
  - Media Server
  - OS X
  - ubuntu
---
I&#8217;ve never been completely happy with my server running Ubuntu 10.04. I do really like the OS but integration with OS X was always a little shaky. Before the upgrade to 10.04 I wasn&#8217;t able to use Time Machine with the network share. After the upgrade I could use Time Machine for wireless back ups but lost the ability to have multiple shares.

Whilst Ubuntu is fairly lightweight it was still running the horribly slow Intel Celeron processor at 100% most of the time which created a lot of heat &#8211; not really good for a server. This was with all the eye candy turned off.

I decided to replace the OS with <a href="http://freenas.org/freenas" target="_blank">FreeNAS</a> as I realised the server was practically just a network attached storage drive. FreeNAS is a free (obviously) operating system that changes any old PC into a NAS with inbuilt support for AFP, Time Machine, UPnP, BitTorrent and rSync. This basically sums up what I was using the server for so FreeNAS is perfect for me.

Installation was quick and easy and after transferring all of the data over I was set up within a few minutes. I&#8217;ve now got multiple shares and Time Machine is backing up to a dedicated back up share. Jordan&#8217;s new Macbook is doing the same.

So everything is running much cooler. The  processor is currently running at 0%! All the things that I wanted to work are working so I can&#8217;t really ask for more!