---
layout: post
title:  "Software Architecture: The Implementation View"
date:   2021-09-20 18:49:31 +0100
categories: stories
thumbnail_image: /assets/img/posts/implementation-view.jpeg
---
![author](/assets/img/posts/implementation-view.jpeg)
[photo source](https://middleware.io/wp-content/uploads/2021/09/What-are-microservices_-How-does-microservices-architecture-work_.jpg){:target="_blank"}

![The 1+4 Model View](/assets/img/figures/1plus4model-implementation-view.png)
*The 4+1 view model describes an application’s architecture using four views, along with scenarios that show how the elements within each view collaborate to handle requests*


# The implementation view
Includes the result of the build process that can be run or deployed such as a Java JAR or Node.js Package. These interact
with each other in the form or a composition or dependency relationship.

##  The Monolithic Architecture Style
Let's extract the definition of the monolithic architecture from an example. Imagine you are invited to develop an enterprise application for
managing music concerts ticketing, One of the requirements is to access the system from the browser and a mobile native application. SO the application
will handle HTTP requests, executing function and accessing a database to persist the data. One of the design options we may have
is to create different components each one is responsible for a specific business logic (event subscription, payments, ticket editing ...). if we choose to develop with
java programming language and the spring framework, we'll have one application with many modules interconnected and coupled to accomplish
the job. But what about the deployment? what type of build output will generate and how to deploy it into production environment.
The answer is we will generate a single Java WAR file.
![author](/assets/img/figures/monolithic-architecture.png)
*The monolithic representation of our example application (Music Event Application) where we can distinguish bounded functions of the system but all in one artifact*

This is what monolithic architecture is about to define the output of your source code as one piece that you can easily:
* Deploy (push or put into the production environment, or any other environment such as development or staging)
* Scale (run multiple instances of the application in response to increasing traffic)
* Debug (in case of non-normal behaviour of the system you can explore the logs, check the config and so on to find the error, all these things are on the same process)

- Question: Now the system is up and running, but a new feature is required which needs to update the payment provider within our application, how can we achieve that?
- Answer: we have to update the source code, re-build the whole application, think a deployment strategy to ensure service continuity of our application

In the context of our monolithic application, there many drawbacks rising while changing a small piece of the system:

- Even though the change concern on one part of the system, this one become indivisible and decoupled, the build and deploy process is slower because all the source code should be re-build to generate the new artifact (Java WAR file)
- The whole system is developed with one stack which limits the on-boarding of other developers with different backgrounds
- Less reusability of the components.
- Increasing the artifact (build output) volume.
- Reliability as one bug in the ticket editing component can cause the whole system to shut down.
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
