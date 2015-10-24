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

Unfortunately we ended up with a couple of problems that have lead to intermittent build failures caused by the [Grunt plugin](https://github.com/gruntjs/grunt-contrib-jasmine) used to run Jasmine tests. As I'm leaving this job in a weeks time I decided its time to get these problems fixed or at least sorted enough to last until the eventual swap to Gulp which is being seriously discussed.

The first issue that has been most relevant recently is the fact that the Phantom.js NPM module used to actually run the Jasmine tests downloads the Phantom.js executable from the BitBucket when it installs. BitBucket has been down a lot recently which has caused a lot of broken builds. I'm not quite sure why it can't just be packaged up with the rest of the module. The Jasmine plugin makes no mention of this in its documentation and we only noticed it was happening when we got some failed builds. After looking through the dependencies we discovered the solution. We need to set an environment variable to point to an internal file server hosting Phantom.js.

```
PHANTOMJS_CDNURL=http://someinternalserver/phantomjs
```

Not exactly a difficult fix but the fact there's no mention of it in projects making use of this module is a bit annoying. So I set this on the parent Team City build configuration and all was well.

Now the second issue required a little more digging around and learning about NPM which I suppose is a good thing in the long run. After running the Jasmine tests we sometimes get an EBUSY error when unlinked a temporary file. The module that sits between the Grunt Jasmine plugin and Phantom.js is called [grunt-lib-phantomjs](https://github.com/gruntjs/grunt-lib-phantomjs). After digging around in the code I found that this temporary file is sometimes being unlinked before the process is done with it. This is fine on UNIX platforms but Windows really doesn't like it.

I had a go at fixing the issue and submitted a pull [request on GitHub](https://github.com/gruntjs/grunt-lib-phantomjs/pull/88/commits). The change works for the Jasmine plugin but unfortunately the QUnit plugin that also uses grunt-lib-phantomjs wasn't fixed so I closed the PR until I can have another go at fixing it.

As my change fixed our issue I wondered if I could point our builds at this patched version of the plugin as a temporary fix. After a bit of Googling I came across [NPM Shrinkwrap](https://docs.npmjs.com/cli/shrinkwrap). This allows you to override version of transitive dependencies of your module. Excellent! I also discovered that you can provide a file path instead of a version number. Doubly excellent! We have a Maven project that contains a bunch of your front end setup stuff like eslint configuration that gets unpacked into the target directory. I added the patched grunt-lib-phantomjs to this project so it'll be downloaded at build time. I then pointed the Shrinkwrap file at this folder and lo and behold it worked.

I'll update this post with the contents of my Shrinkwrap json file on Monday when I'm in the office to better illustrate what I did.

So between these two changes I'm hoping I leave this job with some relatively stable front end builds, at least until the move to Gulp where hopefully the Jasmine plugin won't rely on Phantom.js which seems to be a bit of a pain. 
