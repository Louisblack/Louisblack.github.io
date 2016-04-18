---
title: The Benefits of Immutable Objects
author: louis
layout: post
permalink: /2016/04/immutability
categories:
  - Programming
tags:
  - Programming
  - Java
---
I've recently started working on a new project at my current client that uses Spring MVC to create a REST interface. I've worked with Spring MVC before but not to this extent. The web framework I was using before was completely bespoke. It's JSON handling was done using JSON-lib - a very basic library that hasn't really been looked after. MVC uses Jackson. JSON-lib is a bit like Hibernate in that in requires your classes to have a default constructor and getters and setters for your properties. What inspired me to write this post was the discovery that Jackson is far smarter then deserialising JSON into Java objects. For example we can annotate a constructor...

```java
@JsonCreator
public Person(@JsonProperty("name") String name,
              @JsonProperty("age")  String age) {
    this.name = name;
    this.age = age;
}
```
Instead of requiring a default constructor and setters, Jackson just calls the constructor with the correct values. This means we can delete our setters and create an immutable object. Which is an absolutely massive bonus. Jackson also supports the JsonCreator annotation on static factory methods and even builder classes which we'll come back to later.

But why is immutability a good thing?

Immutability simplifies things a lot. For example, if we have an instance of the person class above, we know when it's contstructed what its state is. That state will never change. If you create a class that provides setters then you sure as hell know that someone is going to use them and they might use them badly which would be your fault.  I've spent too much time trying to work out where and why an object's state has changed between its construction and another point in the code. It's easy to miss a single call to a setter. It makes much more sense to construct your object in the correct state and have done with it.

Immutability simplifies threading. An immutable class is inherently thread safe. If its state cannot change then we cannot have race conditions between threads accessing it. The Java Memory Model even [guarantees visibility of fields marked final across threads](http://www.ibm.com/developerworks/library/j-jtp03304/#4.0) so we don't have to use synchronized or volatile keywords.

[The garbage collector loves immutable objects](http://blog.takipi.com/5-tips-for-reducing-your-java-garbage-collection-overhead/) as they are far more predictable in terms of generations. All objects within the immutable object must have been created before its construction was completed.

Obviously not every object can be immutable otherwise our applications wouldn't do much but we should also favour immutability until the point at which we absolutely need to start editing state. Mutability should never be the default so thing twice before generating setters for all of your properties.

Before I finish I wanted to quickly go back to the builder pattern I mentioned earlier. This is probably my favourite design pattern (having a favourite design pattern is a bit sad I know). If we have a class with lots of properties then we don't particularly want a constructor with 10 or so parameters. It's ugly and easy to screw up when calling it.

Instead we can provide a builder. A builder allows us to gradually build up our state until we are happy and then construct an immutable instance. Here's an example with just a few properties but it works best with many.

```java

    Person person = Person.builder()
        .withName("Louis")
        .withAge(31)
        .build();

```
If we had 10 different parameters to set then you can see how this would be much harder to screw up than trying to remember the order of 10 constructor arguments.

The disadvantage is that it increases the amount of code within the class by quite a lot. Luckily many IDEs have plugins to generate builders automatically so it's pretty quick to do. If you add a property then just delete the builder and regenerate one from scratch.

Here's the class code.

```java

public class Person {
    private final String name;
    private final int age;
    // more properties excluded

    private Person(String name, int age) {
        // private constructor
        this.name = name;
        this.age = age;
    }

    public static PersonBuilder builder() {
        return new PersonBuilder
    }

    public class PersonBuilder {
        private String name;
        private int age;

        private PersonBuilder() {
            // private constructor
        }

        public PersonBuilder withName(String name) {
            this.name = name;
            return this;
        }

        public PersonBuilder withAge() {
            this.age = age;
            return this;
        }

        public Person build() {
            return new Person(name, age);
        }
    }
}

```
