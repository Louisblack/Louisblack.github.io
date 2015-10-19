---
title: 'Building a Media Server &#8211; Installation of Hard Disks and Powering On'
author: admin
layout: post
permalink: /2010/04/building-a-media-server-part-3/
categories:
  - Geek
  - Media Server
tags:
  - computers
  - Final Fantasy
  - Geek
  - linux
  - Media Server
  - XBox 360
---
My first terabyte hard drive arrived the other day. Excitedly I installed it in my server but I was quickly disappointed when it wasn&#8217;t recognised in Ubuntu&#8217;s disk utility. I tried swapping SATA ports on the motherboard and quickly discovered that the second SATA port is broken&#8230; bugger.

So I went on to Amazon and ordered a PCI 4 port SATA card that was Linux compatible. I was going to buy it at some point anyway but I was hoping I could hold off for a while and use my external hard drive for the media back up disk. Due to my impatience I decided to take up Amazon&#8217;s offer of a free month of Amazon Prime (free one day delivery). All went well and I collected the card from the depot the next day.

So today I installed the SATA card and plugged in the 1TB hard disk which was recognised straight away. Hurrah! All i had to do then was add a couple of folders to my Netatalk (open source implementation of the Apple Filing Protocol or AFP) config file and up popped the server on my Finder side bar.

<img class="alignnone" title="finder" src="http://www.louishoughton.com/images/serverpics/finder.jpg" alt="" width="640" height="327" />

Now what&#8217;s the best thing about creating this kind of network? Naming all the computers of course! I decided to name everything after towns in Final Fantasy VII. The server is obviously called &#8216;Midgar&#8217; after the main city. I haven&#8217;t yet decided between Wutai or Junon for the Macbook Pro. If I ever buy myself a computer for the living room I&#8217;ll call that &#8216;Gold Saucer&#8217;.

The rest of the day was spent copying hundreds of gigabytes of videos and music over to the server. I connected everything up with ethernet to take advantage of the increased speed over wireless but it still took hours. Everything is copied now though so I just need to sort out the back up of the media drive and start testing out <a href="http://www.apple.com/macosx/what-is-macosx/time-machine.html" target="_blank">Time Machine</a> (Mac back up utility) with the network share. Time Machine isn&#8217;t designed to work over network by default so it could all go horribly wrong. If it does there is always <a href="http://www.bombich.com/" target="_blank">Carbon Copy Cloner</a>.

And for people that like to look at cables here is &#8216;Midgar&#8217; derobed&#8230;

<img class="alignnone" title="insideserver" src="http://www.louishoughton.com/images/serverpics/insideserver.jpg" alt="" width="640" height="480" />