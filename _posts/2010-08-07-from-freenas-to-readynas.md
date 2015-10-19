---
title: From FreeNAS to ReadyNAS
author: admin
layout: post
permalink: /2010/08/from-freenas-to-readynas/
categories:
  - Geek
  - Media Server
tags:
  - Apple
  - computers
  - freenas
  - Geek
  - linux
  - Media Server
  - ReadyNAS
---
Anyone following the geeky posts on this blog will be aware that I&#8217;ve had a bit on an <a href="http://www.louishoughton.com/category/geek/media-server/" target="_blank">ongoing saga</a> with trying to add storage to my network for media serving and wireless back ups. Recently this task has been achieved using an old PC running FreeNAS. Basically FreeNAS is an operating system that gives an old PC the features of a fairly high end NAS drive. It supports AFP, Time Machine, rSync, even Active Directory which you would usually consider a feature exclusive to Windows Server. The software is very nice but my issue was with the old and unreliable hardware I was running it on. Even running such a lightweight OS things kept dying.

I had been shying away from a proper commercial NAS because of price. Generally the cheaper models don&#8217;t support Mac protocols which makes transfers slower and less reliable. After finally being defeated with FreeNAS I started looking into the Netgear ReadyNAS series. I found that the entry level model with no drives wasn&#8217;t hugely expensive and I figured that the lower running cost and lack of stress would be worth the price.  So I went and ordered myself a ReadyNAS Duo.

After copying my data from FreeNAS onto an external hard disk (formatted in EXT2, the file system recognised by ReadyNAS) I removed the 1TB drive and installed it into the ReadyNAS. I went through the start up wizard which allowed me to disable CIFS (Windows networking protocol) and set up my shares and users. I also enabled Time Machine support. After set up I couldn&#8217;t access the shares. Even when choosing &#8216;Go&#8217; &#8211; &#8216;Connect to Server&#8217; from the Finder menu bar and entering the IP address I could only connect to my user directory, not the &#8216;Media&#8217; and &#8216;Back Up&#8217; shares. After much fiddling and a couple of factory resets I was no closer to solving the issue.

At this point I had a Google around but couldn&#8217;t find anything directly relevant to my situation. What I did find was a few people asking where ReadyNAS places Time Machine back ups. I had just assumed I would use my Back Up share but it seems that when enabling TM support you also create a new (hidden) user called ReadyNAS with its own user directory in which ReadyNAS places the sparse bundles that TM creates.

This got me thinking. Rather than creating proper shares I could create a user called Media. I knew I could connect to user directories so all would be fine. This, however, didn&#8217;t as Finder will only allow you to use one login per network share it would seem (I could be wrong, but this was my experience after trying for 30 minutes). I decided to create one user called Midgar and just lump everything in there and hope for the best. It&#8217;s not quite as elegant as having two separate shares but at least it would work. I now have have to log in as &#8216;Midgar&#8217; and on that one share I have the TM sparse bundles and my media folder. This is a far cry from the user friendly setup I had envisioned and I&#8217;m sure it would turn off many non techy people.

I&#8217;m not sure if I&#8217;m the only one having this problem or if I&#8217;m doing something wrong along the way. I did set it up using the wizard and only delved into the advanced options when things wouldn&#8217;t work. The interesting thing is that this is exactly the <a href="http://www.louishoughton.com/geek/media-server-upgrading-to-lucid-lynx-and-troubles-with-netatalk/" target="_blank">same issue</a> I was having when I upgraded my server at the time to Ubuntu 10.04 Lucid Lynx. Google <a href="http://www.readynas.com/forum/viewtopic.php?p=216670" target="_blank">confirmed</a> that the ReadyNAS is indeed using Netatalk for its AFP implementation. I have no issue with companies using open source software to power their devices but you would think that Netgear with its R&D budget would be able to take Netatalk, improve it to make it more friendly and feature rich then give it back to the community from which it has benefited so much (the ReadyNAS series run a flavour of Linux and use a huge amount of open source software). To be honest I haven&#8217;t actually looked into if they do (I&#8217;ve been too busy trying to get the thing to work) but I would be surprised if they gave the project the support it deserves.

So yeah, one of the reasons for buying the ReadyNAS, reducing stress, hasn&#8217;t really worked out but at least its using less energy.