---
title: Building the Test Pyramid
author: Louis
layout: post
permalink: /2017/10/test-pyramid
categories:
  - Programming
tags:
  - Programming
  - Testing
---

Most people that I've worked with over the years will tell you that I'm
interested in testing. In a world of fast development testing becomes almost as
integral to software delivery as actually writing the code. Sometimes
lacking a feature is better than having that feature but it being buggy or insecure. And while there is still definitely a place for manual testing,
a good suite of automated tests that you can run after every code change allows
developers to make changes with confidence and gives the business confidence to
release those changes to users.

The test pyramid in the title of this post refers to a concept introduced by
[Mike Cohn](http://www.mountaingoatsoftware.com). The idea is you have lots and lots of unit tests (the large base of the pyramid), fewer integration tests and finally a few end to end browser tests (the small tip of the pyramid). As you move from the bottom of the pyramid to the top you become more and more confident that your code works and, crucially, all your parts work
correctly together. It may then seem like the end to end tests are the most
important and that we might as well just implement those but these tests are slow
and much less deterministic than unit tests which means when they break it's
more difficult to know why they broke. Unit tests on the other end of the scale
are fast and isolated so if one fails it's fairly easy to work out what caused
the failure.

In this post I want to write a little about the things I've seen work and the
things I've seen fail when trying to realise a good test pyramid.

**Unit Tests**

***Test Driven Development***

Good test coverage starts before you've even written a line of code. Before
you code you need to know what you want to get out of that code and writing
a unit test is a good way work out your expectations.

There seems to be a lot of push back around Test Driven Development nowadays but I still think it helps produce better quality code because it forces the developer to think about their inputs, outputs and dependencies. Code written after the tests is inherently more testable and testable code tends to be better code because it's made up of smaller classes with fewer dependencies and smaller methods that take fewer arguments. These are all easily quantifiable measures
of code quality.

***Domain Driven Design***
