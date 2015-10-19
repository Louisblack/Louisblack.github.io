---
title: 'ReadyNAS &#8211; Impressions after a few weeks'
author: admin
layout: post
permalink: /2010/08/readynas-impressions-after-a-few-weeks/
categories:
  - Geek
  - Media Server
tags:
  - Apple
  - computers
  - Media Server
  - ReadyNAS
---
A few weeks ago I replaced my FreeNAS network storage with a Netgear ReadyNAS. My <a href="http://www.louishoughton.com/geek/from-freenas-to-readynas/" target="_blank">first impressions</a> weren&#8217;t great. I was hoping for a stress free experience where by I plugged the drive and I instantly had access to network shares for media sharing and Time Machine back ups. I wanted this using AFP, not CIFS, so I get the nice Apple Display icon in my Finder sidebar, not a generic, blue screen of death PC icon.

I&#8217;ve mostly got things sorted out and working the way I want them. Shares are mounting reliably every time although this was accomplished by turning on CIFS sharing. Now I&#8217;m not actually connecting using CIFS. I&#8217;m still connecting via AFP but things just work a lot smoother when CIFS is turned on. I get the nice icon when the shares are mounted but every so often the blue screen icon does rear its ugly head.

For media serving I&#8217;ve installed the ReadyNAS version of <a href="http://www.twonky.com/" target="_blank">Twonky</a> media server. I bought a license when I was running it on Ubuntu a few months ago so it&#8217;s nice that that money wasn&#8217;t wasted. I really like the Twonky software. The web interface is very clean, easy to use and its implementation of UPnP works well with the XBox 360. Downloading is being handled by the ReadyNAS version of <a href="http://www.transmissionbt.com/" target="_blank">Transmission</a>.

On the back up front, Time Machine is working nicely and backing up to its very own Back Up share. The ReadyNAS itself is backed up to an external USB drive every morning at 3am.

After a bit of fiddling I&#8217;ve managed to get things working pretty much as I&#8217;d like. I&#8217;m still a bit annoyed I have to have CIFS turned on to get the shares appearing properly. I&#8217;ve been looking into the application <a href="http://bonjourmounter.gestosoft.com/" target="_blank">Bonjour Mounter</a> that automatically mounts shares when available so that might help. I also made sure I kept the default share names when I set the NAS up (after the forth factory reset) so the share names are in lowercase which annoys me for some reason. I&#8217;m too scared to change them as when I did this before the shares just plain disappeared.

So I&#8217;m relatively pleased with everything. Im sure if I was using Windows things would be much easier to set up. Mac compatibility can be a little flakey but overall, for the price, the ReadyNAS is a pretty good deal.