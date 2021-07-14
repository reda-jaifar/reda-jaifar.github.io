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

# TDD: Test Driven Development
Since its apparition there is many books have been published, I recommend to read one or more to understand this philosophy in deep and acquire
a solid skills for writing tests, Here is my must-read <span style="color:blue">**Test Driven Development By Example**, __Kent Beck__ </span>

>I'll define TDD as a programming style in which production and test code are written together, with the production code
> just after the test one.

By now we described the TDD, there are some rules to take into consideration:
    * Rule one:     We don't write production code before we've written a failing test.
    * Rule two:     We don't write additional tests than sufficient to implement our first scenario of a use case.
    * Rule three:   We don't write more production code than needed to pass the currently failing test.
    
As the TDD is relatively becoming a mature discipline, it started encouraging further innovations derived from it, such BDD
whose main goal is to get developers, testers and people from the business to talk to each other. In other words 
> the real intent is to try and work out what your customer or business wants from the software before you start working on it

Once we adopt the TDD and start working this way with testing side by side with production code, we'll write many tests
per use case or (feature), and more by component and you can imagine the numbers of lines we'll end up with,
managing tests code became as important as production one. I encourage to keep tests clean.
__what makes a test clean? Readability, shortness and expressive. The following snippet shows an example of a test written
with the intention to make it clean, but surely the is no perfect example to follow, just keep in mind to give yours test code your attention.
```java
@Test
  public void testAcceptBooking() {
    // given a booking id
    BookingId bookingId = "48e58688-adc2-4e3d-be9d-f5129723b351";

    // when
    Either<AcceptBookingError, BookingResponse> either = acceptBookingUseCase
                                                          .accept(bookingId);

    // then
    assertThat(either.get().getStatus()).isEqualTo(BookingStatus.ACCEPTED);
  }
```
There is another concept that makes our tests more readable, convenient, and easier to maintain, **Domain-Specific Testing Language**
The idea is to create a set of functions and utilities to hide the details of implementation of your test, the example above we can write
it this way
```java
@Test
  public void testAcceptBooking() {
    giving()
        ._a_bookinId()
    .when()
        .we_accept_a_booking()
    .then()
        .the_booking_should_has_accepted_status();
  }
```

As described by __Robert Martin__ in his book __Clean Code__ a clean test follow other rules that form the F.I.R.S.T acronym

    - Fast: Tests shoud be fast
    - Independent: Tests should not depend on each other
    - Repeatable: Tests should be repeatable in any environment
    - Self-Validating: The tests should have a boolean output
    - Timely: Tests should be written before production code.
    
Finally, we want to think about tests as the compass to reach our destination which is the final secure, viable, and high-quality product we want to build.

----
* [Martin Fowler's blog](https://martinfowler.com/testing/){:target="_blank"}
* [Clean Code Book by Robert C.Martin](https://www.pearson.com/us/higher-education/program/Martin-Clean-Code-A-Handbook-of-Agile-Software-Craftsmanship/PGM63937.html){:target="_blank"}
* [Cucumber Blog](https://cucumber.io/blog/bdd/intro-to-bdd-and-tdd/){:target="_blank"}
* [Agile Alliance](https://www.agilealliance.org/glossary/tdd/){:target="_blank"}
