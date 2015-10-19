---
title: 'Building a Media Server &#8211; Ideas and Preparation'
author: admin
layout: post
permalink: /2010/02/building-a-media-server-part-1/
categories:
  - Geek
  - Media Server
tags:
  - computers
  - Geek
  - linux
  - Media Server
  - OS X
---
My iMac&#8217;s third birthday is fast approaching and as a thank you for three years of loyal service and enjoyable computing I am planning on selling it. It is starting to feel a little long in the tooth &#8211; the 2.16GHz Core 2 Duo is starting to feel a little sluggish and I would really like more than 3GBs of RAM. We are also moving into a smaller place in a monthish so I shan&#8217;t have enough room for a proper desktop. My plan is to sell the iMac on eBay or Gumtree for (hopefully) around £450 and then pay the difference on a 13&#8243; Macbook Pro (when they are finally updated).

I have never had just a laptop and it brings up some issues. The main being a lack of large, always on storage. My iMac currently sleeps rather than being fully powered down which means I can wake it up remotely using an iPhone app and then stream my large music and video library to my XBox 360 connected to the living room T.V. This would be a little inefficient with a laptop as it has a smaller hard drive, it isn&#8217;t always available to be woken up (cannot be done over wifi with my router) and wifi sucks for media streaming.

So in comes the idea of a media server that I can hide out of the way in another part of the house that it still wired up to the network. The plan is to fill it with several large drives &#8211;

160GB &#8211; System (Ubuntu Linux)  
1TB &#8211; Media  
1TB &#8211; Media Backup  
1TB &#8211; Backup for laptops and system drive

The media drive and lap top back up drive will be shared via AFP (Apple Filing Protocol) using <a href="http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/" target="_blank">this incredibly helpful guide</a>. I will use [Rsync][1] to back up the media drive overnight.

XBox media sharing will be done by using [Twonky Media Server][2]. I did have a look around at free and open source alternatives but the ones available all had fairly major drawbacks such as not understanding ID3 tags on MP3s. I managed to pick up Twonky for £10 as they are currently offering it half price. It seems to work as advertised with very little tweaking. Apparently it supports many other devices so it gives me an option to grow.

The system is running on a 2.8GHz Celeron processor with 512MBs of RAM. It seems to be running quite nicely although the graphics card isn&#8217;t recognised and even with the NVidia driver I cannot get higher than 800 x 600 resolution. It&#8217;s not really an issue on a server though when most interaction will be done through web interfaces and SSH.

So far I have only the system set up. AFP and media sharing are working nicely. I&#8217;m going to keep an eye of drive prices and see if I can pick up a bargain once the Macbook is bought. I also need to pick up an SATA PCI card as the motherboard only has two SATA ports.

I&#8217;ll try to keep the blog updated with my progress just in case anyone out there fancies giving it a go as well.

 [1]: http://samba.anu.edu.au/rsync/
 [2]: http://www.twonkymedia.com/