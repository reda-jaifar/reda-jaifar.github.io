---
layout: post
title:  "Software Architecture: The Logical View"
date:   2021-10-17 12:49:31 +0100
categories: stories
thumbnail_image: /assets/img/posts/logical-view.jpeg
---
![author](/assets/img/posts/logical-view.jpeg)
[photo source](https://dz2cdn1.dzone.com/storage/article-thumb/8685724-thumb.jpg){:target="_blank"}

![The 1+4 Model View](/assets/img/figures/1plus4model-logical-view.png)
*The 4+1 view model describes an application’s architecture using four views, along with scenarios that show how the elements within each view collaborate to handle requests*


##  The layered architecture style
This is my first architecture style I've discovered 10 years ago thanks to my java enterprise application course teacher, Ths idea
consist of organizing the elements of an application into layers. Those elements could be java classes grouped by the responsibility type
they manage and respect the rule that each layer should depend only on the layer below it, Another version also tolerate that a layer can
depends on the any of the layers below it.

Even though we can apply this architecture style to any of the 4 model view we've seen above, It is most likely to be used in the logical view
as follows:

* __Presentation layer__: groups classes & interfaces that handle the UI interactions, Such as desktop application UI that handles user interactions like Click, Press, etc...
* __Business logic layer__: contains classes where we implement the business logic of the system. For example classes that calculate the shortest route for delivering merchandise from stock house to customer.
* __Persistence layer__: contains interfaces and classes that interact with database or file system. For example classes that communicate with a MySQL database.

![3 Tier Java Application Architecture](/assets/img/figures/n-tier-architecture-style-java.jpg)
<i>In the above figure, we illustrate the 3 tier architecture for a java application, classes of the same layer are grouped using packages.Note that architecture is beyond
any programming language, so for example in case of a C# application we group classes in namespaces instead of packages for java.</i>

The years go by and the software development community began to recognize some drawbacks of N Tier architecture, below we list some of them:

- __Single Presentation Layer__: With the evolution of the web and mobile applications, many systems provide the same functions, For example a desktop application
    for logistics providing the feature of calculating the shortest route and cost of a delivery, While the business logic remains the same, 
    the interactions with the system are evolving with mobile and web users.
- __Single Persistence Layer__: Modern systems needs to interact with many and/or different storage systems rather than one database.
- __Layer dependencies__: As the business logic depends on the persistence one, we are prevented from testing the business logic in an isolation.

These disadvantages lead to an alternative architecture style we present next.

## The Hexagonal Architecture Style
This architecture style organizes the logical view in a way that puts the business logic at the center. In contrast to the layered
architecture that has a presentation layer, we have here one or more inbound adapters that handle requests from the outside by invoking
the business logic. The same applied to the persistence layer, the application has or more outbound adapters that are invoked by the business logic and invoke external applications.
The main characteristic of this architecture style is that the business logic doesn't depend on these adapters, instead they depend on it.
The Business logic has one or more ports.A __port__ defines a set of operations and is how the business logic interacts with
what's outside it. For example in java these ports are a Java Interface. we distinguish inbound and outbound ports. An inbound port is an API exposed by
the business logic, which enables it to be invoked by external applications, for example a REST API.An outbound port is how the business
logic invokes external systems like Database Access Repositories.

Like the ports there are inbound and outbound adapters. An inbound adapter handles requests from the outside world
by invoking an inbound port. For example in the case of a Java Web Application using Spring framework, An inbound
adapter is a Rest Controller that will invoke inbound port exposed by the business logic.
An outbound adapter implements an outbound port and handles requests from the business logic by invoking an external
application or service.An example of an outbound adapter is an Event Publisher to Kafka or any other Event streaming system.

![Hexagonal Architecture](/assets/img/figures/hexagonal-architecture.jpeg)

*The Figure above shows an example of the hexagonal architecture where the business logic has one or more adapters to communicate with external systems*

Let me remind you that decoupling the business logic from the presentation and data access is the important benefit
of the hexagonal architecture style. This is very useful also when it comes to testing as you can use <abbr title="Test Driven Development">__TDD__</abbr>
easily as you can test your business logic in an isolation.It also defines new model for the modern applications where the 
business logic can be invoked by multiple adapters each one of them invokes an external system.

> The Hexagonal Architecture style is well fit to define the architecture of each service in a microservice architecture.

Both the layered and hexagonal architectures are a set of constraints and rules on how elements within the logical
view are connected and how they communicate.

----

* [Software Architecture Definition by Wikipedia](https://en.wikipedia.org/wiki/Software_architecture){:target="_blank"}
* [The “4+1” View Model of Software Architecture by Philippe Kruchten](https://www.cs.ubc.ca/~gregor/teaching/papers/4+1view-architecture.pdf){:target="_blank"}
* [Advancing the Practice of Software Architecture by Software Engineering Institute](https://www.sei.cmu.edu/our-work/software-architecture/){:target="_blank"}
