---
title: Beyond the Basics of Java
author: Louis
layout: post
permalink: /2017/02/beyond-the-basics
categories:
  - Programming
tags:
  - Programming
  - Java
---

Over the last few years, I've been asked by several friends about learning to code - 
specifically where to start and where to go once you've learnt the basics. It's definitely
a daunting process when you first start because there is so much to learn. Whilst you never
stop learning if you want to be a good developer, it does start getting easier to keep up
with progress. Here I'll try and put down some thoughts on how to learn the basics and 
move on to building proper applications.

***Learn the Basics***

It's never been better to learn a programming language. There are several great websites 
that allow you to complete interactive tutorials by typing code into a website. There's
no need to install anything or set up a development environment which is a massive 
advantage. The first language I learnt was SQL. Setting up mysql and getting to a point 
where you can actually run some SQL statements is surprisingly hard for a newbie.

Websites likes [Codecademy](https://www.codecademy.com) and 
[Learn Java Online](https://www.learnjavaonline.org) are good starters. These should give 
a good idea of concepts and what the code actually looks like. Complete the tutorials on 
these sites and go through the [Oracle tutorials](http://docs.oracle.com/javase/tutorial/java/)
and you should have a decent grasp of the language fundamentals.

At this point it's important to remember that Google is your friend. Every issue you come
across while learning has probably been experienced by another programmer at some point. 
If you get an error message you don't understand then Google it exactly and see what comes 
up. Try not to ask a question on a forum or [Stack Overflow](http://stackoverflow.com) 
without first looking for the answer yourself.

***Choose an IDE***

You can write Java code in Notepad on Windows and manually compile your files but only the 
purest of purists would do that. Most Java (and increasingly other languages) developers 
use an IDE (Integrated Development Environment). This usually combines a text editor, 
a compiler and a run time so you can write, compile and run your code from within a single
application. They usually provide you with useful information as you're writing your code
such as flagging misspelled variable names or showing you a list of available methods you
can call on an object. 

Popular Java IDEs include Eclipse (free), NetBeans (free) and IntelliJ IDEA (paid but has 
a cut down free version). When you first start you probably won't worry too much about
the differences and any one will do.

IDEs also help a lot of with writing tests, which brings me onto...

***Testing***

Make learning to test your code a priority. Read about [unit testing](https://martinfowler.com/bliki/UnitTest.html) 
and get into the habit of writing unit tests for all the code you write. 
This skill will put you ahead of 80% of other developers in interviews
Testable code and code that has tests is better code than code that isn't and doesn't.

***Libraries***

Whilst you could build an application from scratch it would be inefficient and error prone.
You'll learn quickly that good developers will know when to write their own code and when
to reuse something that's already been written. Libraries are reusable modules of code that
you can pull into your project to perform a task. Libraries can be things like utilities 
that provide useful utilities or extend the basic Java libraries like Google's 
[Guava](https://github.com/google/guava) or entire 'frameworks' that allow you to build a 
website with only a few lines of your own code like
[Spring Boot](https://spring.io/guides/gs/spring-boot/). There are libraries available that
allow you to access useful information from websites. Websites sometimes publish
an API (application programming interface). This allows people to get at information provided
by the website using a programming language. For example Google provide a 
[geocoding API](https://developers.google.com/maps/documentation/geocoding/intro) that 
allows you to use information from Google Maps. 
When you want to use a library in your project you create a **dependency** on that library. 
 
***Managing Dependencies***

To use a library Java needs to have it on the *classpath*, basically it just needs to 
know where to look to find the code to run. If you were a masochist you could do this
manually, but luckily there are tools to do this for you. [Maven](http://maven.apache.org) 
and [Gradle](https://gradle.org) help you manage dependencies as well as running tasks
like compiling code, running unit tests and pretty much anything else you need them to do.

***Build Something***

With the skills acquired above you should be abe to build something vaguely useful. It might
not be the greatest application in the world, it might not even have a proper graphical 
interface, but it can do something. See if a website you use provides an API with a Java 
library and do something cool with that information.
 
A good suggestion for a project is something that feels achievable but you don't know how
you're going to achieve it. Don't choose to reimplement World of Warcraft. Instead choose
something small but uses some technologies you've not used before.

***Source Control and Continuous Integration***

If you're starting to write non trivial code then now would be a good time to start looking
at source control. Tools like [Git](https://git-scm.com) allow you to track changes to your
code and revert things that break. You may not see the relevance of these tools when
working alone but they become invaluable when working with a team of developers. Learn the
basics of it now. [GitHub](https://github.com) is a website built around Git that allows
developers to publish their Git repositories. Developers can work on projects together,
raise issues on Open Source projects or just back up their code. GitHub now gives you
private repositories for free so you don't have to publish your early code in public.

If you're publishing your code on GitHub then you might as well start using a service like
[Travis CI](https://travis-ci.org) to automatically run all your unit tests whenever you
make a change to your Git repository. You'll be e-mailed if a change you make causes
your code to not compile or a test to fail. This is called Continuous Integration and is
an important part of modern software development.

***Build Something Bigger***
 
Once you've build something you'll probably want to put an interface on to it. Nobody uses
Java to build desktop applications anymore. You're much better spending your time learning
how to build web applications as they are probably the most common use of Java in most jobs.

As mentioned above [Spring Boot](https://spring.io/guides/gs/spring-boot/) is an good way
to build web applications quickly. You'll probably want to spend a bit of time learning
about the Spring Application framework and especially the Spring MVC modules as Spring 
Boot is really just a streamlined way of building a Spring MVC app. For the meantime
ignore any tutorials that use XML for configuration as they'll probably be pretty old.  
Important things to learn about are the concepts of 'dependency injection' (also known 
as IoC or inversion of control), fundamentals of HTTP (GET vs POST, etc) and, unless 
you want to start learning JavaScript, templating engines for dynamically creating HTML. 
If you've never done any HTML then this is a good time to learn as every developer 
should know some HTML.

Add a database to your web application. Databases bring with them a whole loads of extra
stuff to learn. Tables, primary keys, foreign keys, relationships, referential integrity,
views, SQL etc are all things you should learn about. When writing your Java code to
interface with the database look into the 
[DAO pattern](http://www.oracle.com/technetwork/java/dataaccessobject-138824.html).
Your first foray into this could use raw SQL in your Java code executed with JDBC.
If you use a DAO and an Interface then you can easily swap out your JDBC implementation
for something else using an ORM like [Hibernate](http://hibernate.org/orm/).

***Read Books***

Whilst there is a lot of information out there on the web there are still some super
useful books available. [Clean Code](https://www.amazon.co.uk/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882)
by Robert C Martin and [Effective Java](https://www.amazon.co.uk/Effective-Java-Second-Joshua-Bloch/dp/0321356683)
by Joshua Bloch changed the way I write code. I cannot recommend them enough.
 
***Read Blogs***

Being a good programmer is a bit like being a good lawyer or doctor. You can't just rely
on what you learnt at university. You need to keep your knowledge fresh and keep abreast
on new best practices and tools. It can be quite daunting but there are a few good sites
that aggregate important news stories together. Here's a good list to start with. 
[10 Java Blogs to Follow in 2017](https://www.sitepoint.com/10-java-blogs-follow-2017/)