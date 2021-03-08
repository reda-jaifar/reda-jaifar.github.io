---
layout: post
title:  "Software testing from separate activity to core development"
date:   2021-03-06 12:56:31 +0100
categories: stories
thumbnail_image: /assets/img/posts/software-testing-from-separate-activity-to-core-development.jpeg
---
![author](/assets/img/posts/software-testing-from-separate-activity-to-core-development.jpeg)
[photo source](https://www.railwaysignalling.eu/istanbul-ankara-high-speed-railway-aims-to-open-in-february2014/cropped-b-broshure-forside4-jpg){:target="_blank"}

I remember these days when we used to write testing code after implementing the software features to make sure
that the code is working, avoid bugs. Besides, we create some scripts to automate interactions with the program.

Writing testing code was a separate activity from programming.

# Agile redefine our testing philosophy

When Agile was born in early 2000 as the fruit of a working group including Martin Fowler, The manifesto defines how agile methods
will speed up the software development to bring new products to market faster. The testing activity starts taking a new
definition from a side part activity to undistinguished work of software development, Especially with 
the Xtreme programming method that takes the TDD as its core paradigm. We will cover in further detail the TDD in a
dedicated section below, but first, let's review the different types of tests.
> NB: there are plenty of test types we can code and run, in this post, I share with you only the main ones
from a developer's perspective. Below a non-exhaustive list of test types:

     - Functional testing
     - Load and stress testing
     - Usability testing
     - Security and Vulnerability testing
     - Monkey testing

## Unit tests
This type of software testing cover small and isolated components of software to make sure they behave as expected,
Nowadays these code fragments are writing by the developer itself while implementing the product's features. There are some
properties that these tests should hold
    * They should be fast.
    * Run frequently as part of the continuous integration process, so they are executed after each commit.
    * They need to be readable, Maintainable, and Trustworthy.
    
## Integration tests
The main role of this type of test to confirm that the independently developed components that compose an application
or a system are working as expected together. For example in a Layered architecture based application, you may what to make
sure that your DAO or Repositories are working fine, or verify the web layer interactions with the business layer are matching
the desired behavior, here where the integration tests come to.

Integration tests may cover a variety  of scenarios, here are some common ones:
    * Testing 2 or more components interactions and data flow
    * Verify the data sent by a component is well-formatted by another one before processing it.
    * Verify components handle cases where they lost connectivity between them.
    
# End to End Tests
They may take also the name of broad-stack tests or full-stack tests, Despite their slow time of execution they constitute
an important value for the product's quality as they test the behavior of the application in a real environment.
They are intended to reproduce the end-user interaction with the product and make sure that every feature is responding as it what designed.
These tests have the advantage of testing the software with all its parts connected, on the other hand, they have the
pain of slower to run and difficult to maintain, the reason why it's recommended to reduce the number of these tests compared to 
unit or integration ones as shown in the following figure:
    
![the test pyramid](/assets/img/figures/test-pyramid.png)

----
* [Martin Fowler's blog](https://martinfowler.com/testing/)
* [Clean Code Book by Robert C.Martin](https://www.pearson.com/us/higher-education/program/Martin-Clean-Code-A-Handbook-of-Agile-Software-Craftsmanship/PGM63937.html)