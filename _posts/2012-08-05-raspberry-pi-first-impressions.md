---
title: 'Raspberry Pi &#8211; first impressions'
author: admin
layout: post
permalink: /2012/08/raspberry-pi-first-impressions/
categories:
  - Geek
---
My Raspberry Pi turned up last week. I actually had to leave it untouched for a few days because it came so quickly (about 4 weeks earlier than I expected) that I hadn&#8217;t got round to buying an SD card. I picked up an 8GB SD card for £3.50 from Amazon which was a bit of a shock after only ever buying overpriced Sony Memory Sticks before.

I downloaded and cloned the Raspbian image to the SD card. After hooking everything up I booted into Raspbian and manually started an X session to see how it performs on the Raspberry Pi&#8217;s modest hardware. I must say that I&#8217;m pretty impressed. Performance is pretty snappy even when web browsing&#8230; well, snappy for 700MHz ARM processor coupled with 256MB RAM.

[<img class="alignnone size-medium wp-image-447" title="pi" src="http://www.louishoughton.com/wp-content/uploads/2012/08/photo-300x224.jpg" alt="" width="300" height="224" />][1]

However I&#8217;m not really interested in using the Pi as an every day computer. I&#8217;ve got a fairly beefy laptop for that. Instead I&#8217;m interested in seeing what it can do and what pieces of hardware I can replace with it.

Due to the Pi&#8217;s size and low power usage it would make a really good Airplay receiver. [I&#8217;ve written about Airplay before][2]. Personally I think it&#8217;s Apple&#8217;s killer feature that is one of the main advantages of keeping an all Apple setup. I used [this blog post][3] to quickly install Shairport (an Open Source implementation of Airplay) on to the Pi. The connection seems pretty solid but audio quality from the headphone jack is pretty awful. I have a spare HDMI port on my surround sound receiver so hopefully bypassing the Pi&#8217;s DA convertor will help.

I&#8217;ve also installed a VPN server on it. When I&#8217;m out of the house I can connect and get access to my network and browse the web through an encrypted link which is nice for unsecured wifi. My iPhone doesn&#8217;t seem to want to connect but my Macbook Pro and work Windows 7 PC seem happy to connect.

Another project I&#8217;ve got my eye on is [raspbmc][4] &#8211; the XBMC media software ported to the Pi. Apparently performance is pretty nice when watching h.264 encoded video.

So far it&#8217;s a pretty impressive bit of kit. The fact it costs £30 is quite amazing.

 [1]: http://www.louishoughton.com/wp-content/uploads/2012/08/photo.jpg
 [2]: http://www.louishoughton.com/2011/04/27/shairport-apple-airplay-streaming-for-free/
 [3]: http://tomsolari.id.au/post/27169019561/airplay-music-streaming-on-raspberry-pi?6d1a9dd8
 [4]: http://www.raspbmc.com/