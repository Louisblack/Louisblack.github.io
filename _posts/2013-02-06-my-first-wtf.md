---
title: My first WTF
author: admin
layout: post
permalink: /2013/02/my-first-wtf/
categories:
  - Geek
  - Programming
tags:
  - bad code
  - java
  - Programming
---
A couple of months ago I managed to get myself a new job as a programmer. It was a pretty great feeling achieving what I had been working towards for the past three years. I&#8217;m a couple of months in and I&#8217;m starting to get the hang of things and feel more comfortable. However, it&#8217;s quite a shock to the system going from the nice, well thought out examples of code seen in textbooks and blog posts to a giant code base  filled with fixes, patches and rushed code.

The culprit that made me write this post was a real corker. Whenever anyone checks in code changes all of the tests are run automatically so everyone can see if the changes broke anything. If a test fails after you&#8217;ve changed something then you generally know that you&#8217;ve done something wrong. I say generally because today I checked in some changes and was faced with a failing test in a completely unrelated project. It&#8217;s a horrible feeling seeing your name next to a bright red test failure.

So I went to investigate the test. It didn&#8217;t look like it used anything I changed but you never know. The test was checking some date validation. A date is valid if it&#8217;s between 90 days old and 90 days in the future. The test expected the result to be valid however it was using a hard coded date as input. The input date was valid yesterday but today was over 90 days on. This meant that the test would fail at least every 180 days unless someone changed the hardcoded date. It also meant that the sap who happened to check in code the day the test date was suddenly invalid was blamed for the test failure!

I did what any self respecting programmer would and fixed the test to use the current date as a seed and then wrote more tests to check 90 days before and after the seed date as well as the other boundary values.

So today I learnt that wild code is very different from textbook code.