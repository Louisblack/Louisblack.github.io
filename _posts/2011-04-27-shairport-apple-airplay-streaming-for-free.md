---
title: 'Shairport &#8211; Apple Airplay streaming for free'
author: admin
layout: post
permalink: /2011/04/shairport-apple-airplay-streaming-for-free/
categories:
  - Apple
  - Geek
  - Linux
  - TV and Hi-Fi
tags:
  - airplay
  - airport express
  - Apple
  - appletv
  - computers
  - Geek
  - linux
---
I used a few hours of this past long weekend to have a play with the recently released program Shairport ([original post][1] and [Github repository][2]). What the program does is emulate Apple&#8217;s Airport Express. As well as being an fairly over priced wireless router and print server, the Airport Express allows you to stream music from iTunes or an iOS device wirelessly to a stereo.

[<img class="size-medium wp-image-318 alignnone" title="iTunes-airplay" src="http://www.louishoughton.com/wp-content/uploads/2011/04/iTunes-airplay-300x113.jpg" alt="" width="300" height="113" />][3]

If you have an Airport Express connected to every stereo in your house you can play music to them all at once, in sync, and have a relatively cheap multiroom music system.

As I have a Linux PC connected to my TV and stereo in the living room I thought I&#8217;d give it a go. Installing is very easy &#8211; you need to download a few Perl modules (perl -MCPAN -e &#8216;install Module::Name::Here&#8217;)

  * HTTP::Request
  * HTTP::Message
  * Crypt::OpenSSL::RSA
  * IO::Socket::INET6

Then just fire up Terminal and type

    apt-get install libssl-dev libcrypt-openssl-rsa-perl libao2 libao-dev libio-socket-inet6-perl libwww-perl avahi-utils make perl shairport.pl

Easy! I&#8217;d recommend actually looking at the installation doc when you download as the code is changing everyday and the instructions above are probably already out of date. There are also instructions for installing on OS X and Windows.

So does it work? Yes it does&#8230; and surprisingly well. I&#8217;ve even created a bash script that runs on start up so I don&#8217;t lose it after reboot. I can also connect fine after waking up from hibernation so I don;&#8217;t have to have the computer running all the time.

Overall, I&#8217;m really happy as it has saved me the £90 I was considering spending on an AppleTV (which can also act as an Airport Express for streaming) just for this feature. I already have Boxee and XBMC installed on the PC and all my music on a NAS but iTunes is really my go to application for music. It doesn&#8217;t suck nearly as much on a Mac as on Windows and all my playlists and podcasts are in it. I&#8217;ll still probably pick up an Express for the bedroom as having to plug a phone or iPod in feels a bit cumbersome.

Lets just hope Apple don&#8217;t attempt to change the key and up security so this stops working. Fingers crossed!

 [1]: http://mafipulation.org/blagoblig/2011/04/08
 [2]: https://github.com/albertz/shairport
 [3]: http://www.louishoughton.com/wp-content/uploads/2011/04/iTunes-airplay.jpg