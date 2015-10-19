---
title: 'Media Server &#8211; Upgrading to Lucid Lynx and Troubles With Netatalk'
author: admin
layout: post
permalink: /2010/05/media-server-upgrading-to-lucid-lynx-and-troubles-with-netatalk/
categories:
  - Geek
  - Media Server
tags:
  - Apple
  - computers
  - Geek
  - linux
  - Media Server
  - netatalk
  - OS X
---
I wasn&#8217;t planning on upgrading my server to the newly released Ubuntu 10.04 (codenamed Lucid Lynx) just yet but after reading many positive reviews I decided to give it a shot. It is after all a Long Term Support release which means that Canonical (the company behind Ubuntu) will be supporting this version for three years as opposed to the usual 18 months.

I decided on using Ubuntu&#8217;s inbuilt Update Manager as I&#8217;ve never experienced any issues with it so far. I also have everything backed up so I could always roll back to 9.10 if anything happened. The upgrade took an age. Bear in mind though that my server is a rather ageing 2GHz single core Celeron with 512MB DDR RAM. It&#8217;s not fast by anyone&#8217;s standards. I left it running over night and when I woke up everything had installed correctly and restarted.

This isn&#8217;t going to be a review or anything as I use my server for serving files and media so I rarely actually look at the desktop.

Now it seems that Netatalk (the open source implimentation of Apple&#8217;s AFP file sharing protocol) is included in this version of Ubuntu which upgraded my 2.0.4 installation. I had tried upgrading Netatalk a couple of weeks ago and gave up due to a username and password prompt when connecting to shares that didn&#8217;t recognise either my server&#8217;s login details or my Macbook Pro&#8217;s. I decided to give 2.0.5 another go seeing as it was already installed.

My shares had stopped working so I ventured into the AppleVolumes.default config file and reentered my shares. They are&#8230;

    /media/storage/Media "Media"
    /media/storage/backup "Back Up"

For some reason this didn&#8217;t seem to work. When using &#8216;Connect to server&#8217; from my Macbook Pro I was able to choose which share to mount but once chosen it would fail.

I spent most of the morning fiddling with options and restarting Netatalk. Finally I realised that mounting the root directory would work correctly.

    / "Root"

I tried /media which again worked. Even

    /media/storage

worked. But as soon as I added the final folder it would refuse to mount. I have had to leave it for the time being. Hopefully someone more clued up on the complexities of Netatalk will be able to shed some light on things.

On the plus side it means that I can finally use Time Machine with the share. This was the feature touted for 2.0.5 which tempted me to upgrade in the first place. Time Machine is far more picky in Snow Leopard than it was on Leopard so just using the terminal command&#8230;

    defaults write com.apple.systempreferences TMShowUnsupportedNetworkVolumes 1

doesn&#8217;t do the trick anymore. Snow Leopard required a lot more work before Netatalk 2.0.5 came along. Now Netatalk basically pretends it&#8217;s a authorised share such as a computer running Leopard or a Time Capsule.

So my upgrade was a half success. On the plus side I can now back up over the network. On the down side I now have to make do with the one network share instead of the nicely organised &#8216;Media and &#8216;Back Up&#8217; ones I had previously. Admittedly the &#8216;Back Up&#8217; wasn&#8217;t really doing much without Time Machine so I supposed I haven&#8217;t lost out too badly.