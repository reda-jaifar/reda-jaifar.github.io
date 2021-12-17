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
- Less re-usability of the components.
- Increasing the artifact (build output) volume.
- Reliability as one bug in the ticket editing component can cause the whole system to shut down.

In the next section, we discuss the alternative and how microservices addresses many of the drawbacks of monolithic and bring new added value but also some very challenging points to handle.

## The Microservices Architecture Style
Microservices architecture style organizes the application as a set of loosely coupled, independently deployable services, Together these services deliver the functional and business
features of the system we want to build. Let's continue with our Music Event Application example and try in the above illustration to define its microservices architecture:

![author](/assets/img/figures/implementation-view-microservices.png)
*The Microservices representation of our example application (Music Event Application) where 3 services communicate through HTTP using REST*

As we can observe in the illustration each service run in independent process and also could have its own database(recommended), Notice also how these services communicate
to each other, in this example I suggest using the REST API through HTTP, but this is not the only communication option we can have, there are more such as messaging using a message broker.

__Let's tackle with further detail the microservices inter-communications in a dedicated article, so far and the rest of this document we will use REST as a reference.__

### What is a service ?
As the word service is a most recurrent when we explore the microservice architecture, Here is a definition:
> A service is an independent deployable application or software component that provides a set of functionalities accessible through an API. A service has its own
> logical architecture, Hexagonal architecture may fit many use-cases ( [read more about Hexagonal Architecture and alternatives in this article]({% post_url 2021-09-19-software-architecture-logical-view %}) )
> in addition a service can be developed with its specific technology stack that may differ from other services`s stack in a microservices architecture

### What is loosely coupled Services and why they should ?
Two services are loosely coupled if changes in the design, implementation or behavior in one __won't__ cause change in others. In microservices architecture coupling will happen when
a change in one enforces an almost immediate change to one or more microservices that collaborate with it directly or indirectly.

While designing microservices architecture and in order to make the services the less coupling possible, consider the following points:
#### <span style="color:blue">Database sharing</span>
the data storage is a microservice implementation details that should be hidden to its clients (usually other microservices). 
If Microservice A needs to access data of Microservice B, B should provide an API that A will use to consume the needed data

#### Code Sharing
By definition microservices do not share codebase, but we may want to avoid redundancy by sharing dependency libraries and
end up needing to update frequently in response to clients change requests. So shared code should be as minimum as possible.
A good practice that may seem strange at glance is to duplicate code so each service has its own copy, so we need to update the library to match Service A requirements, Service B remains un-impacted 


https://www.capitalone.com/tech/software-engineering/how-to-avoid-loose-coupled-microservices/
https://www.edureka.co/blog/interview-questions/microservices-interview-questions/
----

* [Software Architecture Definition by Wikipedia](https://en.wikipedia.org/wiki/Software_architecture){:target="_blank"}
* [The “4+1” View Model of Software Architecture by Philippe Kruchten](https://www.cs.ubc.ca/~gregor/teaching/papers/4+1view-architecture.pdf){:target="_blank"}
* [Advancing the Practice of Software Architecture by Software Engineering Institute](https://www.sei.cmu.edu/our-work/software-architecture/){:target="_blank"}
