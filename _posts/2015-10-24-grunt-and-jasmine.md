---
title: Grunt and Jasmine
author: louis
layout: post
permalink: /2015/10/grunt-and-jasmine/
categories:
  - Programming
tags:
  - JavaScript
  - Programming
---
Being a pretty traditional Java shop, all of our front end packages are built as Maven projects. For a couple of years my team were running our Jasmine unit tests using a [Maven plugin](http://searls.github.io/jasmine-maven-plugin/). This worked but newer versions of the plugin started to require newer versions of Maven that, at the time, we couldn't upgrade to. Last year we migrated our front end build stuff to Grunt using [another Maven plugin](https://github.com/eirslett/frontend-maven-plugin) that allowed us to download node, do an NPM install and then run grunt. This was a huge upgrade and allowed us to starting using cool things like eslint.

Unfortunately we ended up with
