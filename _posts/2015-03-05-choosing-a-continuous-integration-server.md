---
title: Choosing a Continuous Integration Server
author: admin
layout: post
permalink: /2015/03/choosing-a-continuous-integration-server/
categories:
  - Final Project
  - OU Degree
  - Programming
tags:
  - CI
  - OU
  - Programming
---
Before I write any code I want to make sure tests are run, code is analysed for bugs and the formatting checked straightaway and every time code is changed. This means choosing a continuous integration server (or service). The choices are&#8230;

  * [Jenkins CI][1]
  * [TeamCity][2]
  * [Travis CI][3]

&#8216;Jenkins CI is the leading open-source continuous integration server&#8217; (Jenkins-ci.org, 2015). However this should not make Jenkins the default choice. TeamCity is not open source, but licenses for individuals (up to 3 build servers and 20 projects) are free.  TeamCity has the advantage of built in integration with Maven which is the build tool I am using for this project. Jenkins requires a plugin to be installed. TeamCity is also what I use at work so familiarity would be helpful.

TeamCity and Jenkins both have the same down side though. Both will require me to install them on a machine and have them running all day. Not only does this mean keeping my iMac on 24/7 it also means going through the hassle of installing it and setting up a database. Travis CI doesn&#8217;t have this problem because it&#8217;s web based. You just create an account, point it at a Github repo and it&#8217;ll run the command that makes the most sense (mvn test if you have a pom.xml) when it detects a change.

For running unit tests and running static analysis plugins like [FindBugs][4] and [Checkstyle][5] Travis CI should be fine. I may run into problems when I want to do something a little more advanced. [SonarQube][6] is the current top dog for static analysis. It highlights problem areas, measures test coverage and calculates technical debt. It provides a really nice dashboard showing all this data. SonarQube requires the CI server to be able to connect to the SonarQube instance which would be a lot easier (and more secure) if they were both located within the same network. It looks like the [setup for integration tests that use Selenium][7] web driver to fire up a browser and perform actions could be a time sink. I could definitely see a few evenings being lost there.

Due to time constraints it makes most sense to use Travis CI until a something comes up that it can&#8217;t do.

 [1]: http://jenkins-ci.org
 [2]: https://www.jetbrains.com/teamcity/
 [3]: http://travis-ci.org/
 [4]: http://findbugs.sourceforge.net
 [5]: http://checkstyle.sourceforge.net
 [6]: http://www.sonarqube.org
 [7]: http://docs.travis-ci.com/user/gui-and-headless-browsers/