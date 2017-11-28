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

Most people that I've worked with over the years will tell you that I'm interested in testing. In a world of fast development testing becomes almost as integral to software delivery as actually writing the code. Sometimes lacking a feature is better than having that feature but it being buggy or insecure. And while there is still definitely a place for manual testing, a good suite of automated tests that you can run after every code change allows developers to make changes with confidence and gives the business confidence to release those changes to users.

The test pyramid in the title of this post refers to a concept introduced by [Mike Cohn](http://www.mountaingoatsoftware.com). The idea is you have lots and lots of unit tests (the large base of the pyramid), fewer integration tests and finally a few end to end browser tests (the small tip of the pyramid). As you move from the bottom of the pyramid to the top you become more and more confident that your code works and, crucially, all your parts work correctly together. It may then seem like the end to end tests are the most important and that we might as well just implement those but these tests are slow and much less deterministic than unit tests which means when they break it's more difficult to know why they broke. Unit tests on the other end of the scale are fast and isolated so if one fails it's fairly easy to work out what caused the failure.

In this post I want to write a little about the things I've seen work and the things I've seen fail when trying to realise a good test pyramid.

**Unit Tests**

**_Test Driven Development_**

Good test coverage starts before you've even written a line of code. Before you code you need to know what you want to get out of that code and writing a unit test is a good way work out your expectations.

There seems to have been a lot of push back around Test Driven Development lately but I still think it helps produce better quality code because it forces the developer to think about their inputs, outputs and dependencies. Code written after the tests is inherently more testable and testable code tends to be better code because it's made up of smaller classes with fewer dependencies and smaller methods that take fewer arguments. These are all common and easily quantifiable measures of code quality.

TDD takes a bit of practice for developers not familiar with it but it also requires a mind shift for management that see anything that's not writing code for new features as wasted effort. Everyone in the team needs to realise that writing unit tests should be considered a part of the standard development practice even at crunch time.

**_Domain Driven Design_**

This might be a controversial opinion for many Java developers who have grown up developing applications in the Spring Framework and Java EE but I think that proper object oriented design makes code clearer and definitely helps with testing. Many spring applications I work on tend to do the whole controller - service - repository thing with most of the application logic sitting in services and anaemic data and domain classes with only getters and setters. The problem with this approach is that the tests require a lot of mocked dependencies and become hugely brittle because tests need to know about inner workings of the class their testing. Basically if you're having to rely on `Mockito.verify()` to assert something has happened within your class then something has gone very wrong.

**Integration Tests**

Unit tests are super useful but they're not enough on their own. Just because two components work independently it doesn't mean that they'll work properly when interacting with one another.

<blockquote class="twitter-tweet" data-lang="en"><p lang="en" dir="ltr">2 unit tests. 0 integration tests. <a href="https://twitter.com/hashtag/programming?src=hash&amp;ref_src=twsrc%5Etfw">#programming</a><a href="https://t.co/sl0fhiIk6t">https://t.co/sl0fhiIk6t</a> <a href="https://t.co/QQUpFtiCUc">pic.twitter.com/QQUpFtiCUc</a></p>&mdash; Randy Olson (@randal_olson) <a href="https://twitter.com/randal_olson/status/691287668647419904?ref_src=twsrc%5Etfw">January 24, 2016</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>


Integration tests can be difficult to define. The name can refer to tests that test the interaction between two classes, an entire microservice or two microservices. If we were developing an application with Spring Boot an integration test might use `SpringRunner.class` and the `@SpringBootTest` annotation to bring up the application context with all the beans and fire off web requests to a `MockMvc` instance.

**_Micro Services_**

In the world of microservices we will find ourselves depending on other services that we call over HTTP. We should probably test the interactions between services We could use the `@MockBean` annotation in our Spring Boot test above to create a Mockito mock that replaces the real instance of the class that calls the service. This is definitely simple and it'll be fast because it's not actually calling anything. The problem is that it's brittle. A change to the service will not be reflected automatically so we could end up with lots of green tests that are just lies.

A popular solution to this problem is to use Docker and Docker Compose to start all of your codes dependent services at once and run tests against those. You'll get a much more accurate result than mocking because your dependencies are real. The problem with this approach is that it's slow. If a service is slow then your tests will be slow. Also if the service changes its API then your tests may start breaking without you changing any code. This can get depressing very quickly.

A good solution that is both robust and fast is to test against Contracts. [Consumer Driven Contracts](https://martinfowler.com/articles/consumerDrivenContracts.html) allow both to the consumer and producer of an API to work independently. They both test against the contract instead of each other. There are some great CDC frameworks to use nowadays. Pact has been around for a while but Spring Cloud Contracts is a relative newbie. They work by defining a contract in a DSL like so:

```groovy
org.springframework.cloud.contract.spec.Contract.make {
  request {
    method 'PUT'
    url '/fraudcheck'
    body("""
    {
      "clientId":"1234567890",
      "loanAmount":99999
    }
    """)
    headers {
      header('Content-Type', 'application/vnd.fraud.v1+json')
    }
  }
response {
  status 200
  body("""
  {
    "fraudCheckStatus": "FRAUD",
    "rejectionReason": "Amount too high"
  }
  """)
  headers {
    header('Content-Type': 'application/vnd.fraud.v1+json')
  }
 }
}
```

The framework uses the contract to create tests that hit the API and assert that the response matches the expected one. It can also bring up a WireMock server that will return the canned response when it receives a request that matches that of the contract for the consumer to test against. As long as both sets of tests are green then the services should interact with each other properly.

** Browser/UI Tests**

We've made our way to the top of the test pyramid. These tests will give you a really good idea if your code is working properly because it's testing it all together on production like infrastructure. The problem here is that these tests are slow and can be incredibly hard to write in a way so they're not brittle.

Automated browser tests work by selecting elements using CSS selectors and filling in forms or clicking buttons to work through various user interactions. When you write your first one it's a real moment of excitement. You watch with glee as the computer runs through your scenario lightning quick clicking on things and making assertions on onscreen text. You quickly lose that childlike wonderment when you're sitting through 30 minutes of tests waiting to see if your pull request can be merged.

It's tempting when you start writing browser tests to have one per user story. It sounds completely logical to have that as a part of the acceptance criteria but these tests can multiply and become a huge bottleneck in your test pipeline. Instead I've seen a lot of success with browser tests just covering several key user journeys. These journeys will often encompass several user stories but can be run through in a single go to avoid repeating set up like you would have to with multiple independent tests.

It's important not to lump UI component tests in with browser tests. We can create a UI component using Angular or React and write a really fast, decoupled unit test that tests interactions with the component's UI - so if I click this button then this should happen. If you find yourself writing lots of complex browser tests see if you can push that testing into the component itself.

**Final Thoughts**

Wow. This post really blew up. I wasn't expecting to write so much but this is a subject pretty close to my heart. Good testing can make software development a joy. Bad testing can lead to mental breakdown.

The important thing to remember when trying to decide whether to test something in a unit test, integration test or a browser test is to _always_ favour the unit test. Only when you're absolutely sure that you can't test sufficiently at the unit level should you look at integration tests. Then before writing another browser test you should think if you couldn't get the same result from a UI component test and/or an integration test.
