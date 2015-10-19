---
title: Revo R3700, Ubuntu 10.10 and Boxee
author: admin
layout: post
permalink: /2010/12/revo-r3700-ubuntu-10-10-and-boxee/
categories:
  - Geek
  - Linux
  - Media Server
  - TV and Hi-Fi
tags:
  - Boxee
  - computers
  - Geek
  - HTPC
  - linux
  - Media Server
  - R3700
  - Revo
  - ubuntu
---
A few months ago I wrote a <a href="http://louishoughton.com/geek/choosing-a-media-streamer/" target="_self">post</a> about choosing a device for streaming media from the web and the NAS on my network. At the time I was trying to choose between an updated AppleTV and a net top running XBMC. Since then I discovered <a href="http://www.boxee.tv" target="_blank">Boxee</a>. Boxee is built on top of XBMC but incorporates extra social features and makes viewing web based content easier. For a while I considered picking up the dedicated Boxee Box build by D-Link but at £200 I thought it&#8217;d make more sense to buy a Atom based net top and install Boxee on that. That way I get the same functionality but with the option of installing other useful applications.

I quickly realised that the price of the Boxee Box is definitely worth it if you don&#8217;t have time to fiddle. I always knew that running an HTPC (Home Theatre PC) was going to take some time to set up but I still wasn&#8217;t prepared for the amount of hassle.

My first attempt at installation was with Ubuntu 10.10.  Everything went smoothly until I came to shut down after the installer finished. The screen locked up. &#8216;No problem&#8217; I thought and did a hard reset. After installing the NVidia drivers I restarted and it hung again. Turns out the wireless driver for this hardware  in 10.10 has a problem unloading. I couldn&#8217;t find a solution that evening so decided to have a look at Windows XP.

Installation was fine until I was greeted with that long forgotten about issue of searching for drivers. I managed to get everything working and Boxee installed. This is where I find out that Boxee relies on DXVA (Direct X Video Acceleration)  to offload processing to the GPU. This is only available in Vista and Win 7.  Every video played like hell&#8230; even 240p Youtube videos.

In the mean time I managed to stumble upon a fix for the previously mentioned wireless driver bug in Ubuntu 10.10. Post number 9 on <a href="https://bugs.launchpad.net/ubuntu/+source/linux/+bug/662288" target="_blank">this thread</a>. Hurrah! The hard disk was formatted and Ubuntu was reinstalled with the fix doing its stuff. I can now shut down/hibernate/suspend without the system locking.

Video performance is much better under Ubuntu. Boxee in Ubuntu uses VDPAU for its GPU acceleration which is obviously available to 10.10 as it&#8217;s the most up to date release. Flash content can still be a bitch but that&#8217;s down to Adobe not building GPU acceleration into Flash 10.1 on any OS except for Windows. 10.2 fixes this so once that&#8217;s out of beta hopefully Boxee will build it in and even 1080p Flash content will play smoothly.

I was hoping to be able to stream most things wirelessly but  I&#8217;m starting to think my ISP supplied N router has an issue with sustained data throughput over wireless.  I can copy a file from my NAS (gigabit ethernet) to my Macbook Pro (wireless N) and get about 3-4 MB/s. That should be enough for any video file to play smoothly but when watching a DVD rip in Boxee it&#8217;ll stop randomly for a few seconds every 10 or so minutes. I think I&#8217;ll just run a cable round at some point. At least then I can plug in my Blu Ray player and XBox 360 as well.

There are still definite issues with this set up but overall things seem to be running smoothly. I&#8217;ll maybe make another post with my actual views after a few weeks usage. I think once I put down an ethernet run things will become a lot more useful and I can actually make a proper judgement on the set up.