---
layout: post
title:  "Software Architecture: Play With Bricks"
date:   2021-09-18 12:49:31 +0100
categories: stories
thumbnail_image: /assets/img/posts/software-architecture-play-with-bricks.jpeg
---
![author](/assets/img/posts/software-architecture-play-with-bricks.jpeg)
[photo source](https://holition.com/play/ycn-s-lego-serious-play-workshop){:target="_blank"}

# What is Software Architecture?
__The software architecture of a computing system is the set of structures needed to reason about the system, which 
comprise software elements, relations among them, and properties of both.__
<u>by SEI</u>

We can decrypt the above definition as structuring a system as a whole recessed block into parts connected, complementary and modular.
The more these parts are decoupled and can work independently, and communicate to each other effectively the more our architecture
will fill its mission to ensure a maintainable, extensible and homogeneous system.

# The 4+1 view model of software architecture
Like a building, there are different plans and maps that can describe different the different perspectives of that building,
we have the electrical, plumbing, structural and others. This is exactly how the 4+1 view model defines software architecture
in the paper published by [Phillip Krutchen](https://www.cs.ubc.ca/~gregor/teaching/papers/4+1view-architecture.pdf){:target="_blank"}

![The 1+4 Model View](/assets/img/figures/1plus4model.png)
*The 4+1 view model describes an application’s architecture using four views, along with scenarios that show how the elements within each view collaborate to handle requests*

Each of the four views has a well defined purpose as detailed below:
## Logical View
It consists of the source code written by developers, in the context of an oriented programming language like Java, the elements are
classes and packages, in addition to relationships between them such as inheritance, association, and composition...

## Implementation View
Includes the result of the build process that can be run or deployed such as a Java JAR or Node.js Package. These interact with each
other in the form or a composition or dependency relationship.


## Process View
Refer to the process holding and running either in virtual machines or containers like docker, relations between them is called
inter-process communication.

## Deployment View
Represents the map of the physical or virtual machines where the system is executed and running, also describes the communication
at level through the network. For example this view can be a VPC with all the routing configuration inside this network and between it and the internet.

# Why an application architecture is relevant?
An application come to life with the purpose of solving a problem, to do so it needs to fulfill two types of requirements, Functional requirements
that defines what the application should do, Previously defined in the form of specifications, with the __agile__ edge we define them as __user stories__,
__use cases__, or events. we can start coding immediately and produce an application that respond to these requirements without thinking about architecture.
But when it come to develop a reliable, maintainable and extensible system, Architecture is our core activity because it helps us
answer questions regarding how the system behaves with millions of users at the same time, __security threats__ and __delivery time__.
<span style="color:Purple">__Architecture meets quality requirements__.</span>

# Architecture Styles
I found the definition given by David Garlan and Mary Shaw in their publication titled [An Introduction to Software Architecture](https://www.cs.cmu.edu/afs/cs/project/able/ftp/intro_softarch/intro_softarch.pdf){:target="_blank"}
an amazing reference to understand the concept of architecture styles and how it can be view in the field of computing systems.

>An architectural style, then, defines a family of such systems in terms of a
pattern of structural organization. More specifically, an architectural style
determines the vocabulary of components and connectors that can be used in
instances of that style, together with a set of constraints on how they can be
combined. These can include topological constraints on architectural
descriptions (e.g., no cycles). Other constraints—say, having to do with
execution semantics—might also be part of the style definition.

Follow are the questions shared by these two pioneers in the discipline of software architecture, answering these questions
will remarkably help define the architecture that fit for the system we're building:
 
Given this framework, we can understand what a style is by answering the
following questions: __What is the structural pattern__,__the components__,
__connectors__, and __constraints__? What is the underlying computational model?
What are the essential invariants of the style? What are some common
examples of its use? What are the advantages and disadvantages of using that
style? What are some of the common specializations?

Let's explore some of the most known architecture styles

##  The layered architecture style
This is my first architecture style I've discovered 10 years ago thanks to my java enterprise application course teacher, Ths idea
consist of organizing the elements of an application into layers. Those elements could be java classes grouped by the responsibility type
they manage and respect the rule that each layer should depends only on the layer below it, Another version also tolerate that a layer can
depends on the any of the layers below it.

Even though we can apply this architecture style to any of the 4 model view we've seen above, It is most likely to be used in the logical view
as follow:

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

## 

----

* [Software Architecture Definition by Wikipedia](https://en.wikipedia.org/wiki/Software_architecture){:target="_blank"}
* [The “4+1” View Model of Software Architecture by Philippe Kruchten](https://www.cs.ubc.ca/~gregor/teaching/papers/4+1view-architecture.pdf){:target="_blank"}
* [Advancing the Practice of Software Architecture by Software Engineering Institute](https://www.sei.cmu.edu/our-work/software-architecture/){:target="_blank"}
