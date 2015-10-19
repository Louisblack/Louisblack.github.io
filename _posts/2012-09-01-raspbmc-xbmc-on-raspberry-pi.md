---
title: 'raspbmc &#8211; XBMC on Raspberry Pi'
author: admin
layout: post
permalink: /2012/09/raspbmc-xbmc-on-raspberry-pi/
categories:
  - Geek
  - Media Server
tags:
  - Boxee
  - computers
  - linux
  - raspberry pi
  - xbmc
---
I think I may have decided upon a use for my Raspberry Pi. It&#8217;s now running [raspbmc ][1]- a optimised port of the media centre software XBMC. For such a teeny and low powered device it runs it beautifully. Performance is a bit more sluggish than my Acer Revo R3700 running XBMCbuntu but some of the added extras in raspbmc make up for it.

It&#8217;s so good that I&#8217;ve actually decided to sell the Revo and use the Raspberry Pi as my main XBMC machine. OK the Pi isn&#8217;t powerful enough to emulate old consoles like the Revo did but I never really played them anyway. I don&#8217;t even get enough time to play my PS3 and XBox nowadays.

Where the Pi really succeeds is video playback. 1080p videos play smoothly due to hardware decoding of the h.264 video codec. Old non-HD avi files play well too. That tends to sum up my entire video library so it works for me. 5.1 audio decoding works out of the box. I had the Revo for two years and I still had problems getting surround sound (or in fact any sound through HDMI) whenever I installed a new version of XBMC or Ubuntu back when I was using Boxee. Whilst fiddling to get something working can be fun sometimes, I don&#8217;t particularly want to be fixing something when I actually want to watch a film.

Thanks to the newly released HDMI CEC functionality I can even control XBMC with my TV&#8217;s remote control so I don&#8217;t have to buy a separate remote. You can of course use the iOS or Android remote apps which are great in some ways but awful for navigating menus as you have to look down to see where your finger is on the touch screen.

Whilst being able to use my TV remote is great some of the buttons were mapped to strange functions. I had accepted this as one of the very few drawbacks. What I didn&#8217;t realise was that you can map the buttons to whatever the hell you want. All you need to do is edit the remote.xml file. The command below creates one in your home directory from the default XBMC one.

` cp /opt/xbmc-bcm/xbmc-bin/share/xbmc/system/keymaps/remote.xml /home/pi/.xbmc/userdata/keymaps/remote.xml<br />
`  
I then opened the newly created remote.xml in my home directory and added these lines to the <FullScreenVideo> section.  
`<br />
<red>Pause</red><br />
<green>Stop</green><br />
<yellow>ShowSubtitles</yellow>`

`<select>OSD</select>`

The 3 are fairly easy to work out. The <select> section means you can now click the select button to bring up the video controls rather than changing the aspect ratio like it does by default.

YOu can find all the commands on the [XBMC wiki][2].

I&#8217;ve recorded a video to show using my Philips TV remote and what to expect from the Pi. The Inception video at the start is 1080p although it doesn&#8217;t really look like it on camera. The TED video app is a bit slow to list content and start videos but performance is fine once playing the video.

[embedplusvideo height=&#8221;418&#8243; width=&#8221;695&#8243; standard=&#8221;http://www.youtube.com/v/1P12Ev0JcSw?fs=1&#8243; vars=&#8221;ytid=1P12Ev0JcSw&width=695&height=418&start=&stop=&rs=w&hd=0&autoplay=0&react=0&chapters=&notes=&#8221; id=&#8221;ep4483&#8243; /]

 [1]: http://www.raspbmc.com/ "raspbmc"
 [2]: http://wiki.xbmc.org/index.php?title=Keymap.xml#Remote_Section "XBMC wiki"