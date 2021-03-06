---
layout: post
title:  "Software testing from separate activity to core development"
date:   2020-03-10 12:56:31 +0100
categories: stories
thumbnail_image: /assets/img/posts/software-testing-from-separate-activity-to-core-development.jpeg
---
![author](/assets/img/posts/5-years-journey-of-software-engineering.jpeg)

I remember these days when we used to write testing code after implementing the software features in order to make sure
that the code is working, avoid bugs. In addition we create some scripts to automate interactions with the program.

Writing testing code was a separate activity to programming.

#Agile redefine our testing philosophy
When the agile was born a the fruit of a working group including Martin Fowler manifesto that defines how agile method
will speed up the software development to bring new products to market faster. The testing activity start taking a new
definition from a side part activity to undistinguished work of software development. Especially with 
the Xtreme programming method that take the TDD as it's core paradigm. We will cover in further details the TDD in a
dedicated section below, but first let's review the different types of tests we can code.

## Unit tests
This type of software testing cover small and isolated components of a software to make sure they behave as expected,
Nowadays these code fragment are writing by the developer itself while implementing the product's features. There are some
properties that these tests should hold
    * They should be fast.
    * Run frequently as part of the continuous integration process, so they are executed after each commit.
    * They need to be readable, Maintainable and Trustworthy.
    
## Integration tests
The main role of this type of tests to confirm that the independent developed component that compose an application
or a system are working as expected together. For example in a Layered architecture base application, you may what to make
sure that your DAO or Repositories are working fine, or verify the web layer interactions with the business layer is matching
the desired behavior, here where the integration tests come to.

Integration tests may cover a plenty of scenarios, here are some common ones:
    * Testing 2 or more components interactions and data flow
    * Verify the data sent by a component is well formatted by another one before processing it.
    * Verify the our component handles cases where they lost connectivity between them.
    
# End to End Tests
They may take also the name of broad-stack tests of full-stack tests, Despite their slow time of execution they constitute
an important value for the product quality as they test the behavior of the application in a real environment. They intent to 
reproduce the end user interaction with the product and make sure that the features work fine.
These tests have a the advantage of testing the software with all its parts connected, in the other hand the have the
pain of slower to run and difficult to maintain, the reason why it's recommended to reduce the number of these tests compared to 
unit or integration tests as shown the the following figure:
    
![the test pyramid](/assets/img/figures/test-pyramid.png)