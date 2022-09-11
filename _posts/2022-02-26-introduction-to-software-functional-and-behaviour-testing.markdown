---
layout: post
title:  "Introduction to software functional and behaviour testing"
date:   2022-02-26 22:45:31 +0100
categories: stories
thumbnail_image: /assets/img/posts/introduction-to-software-functional-and-behavior-testing.jpg
---
![author](/assets/img/posts/introduction-to-software-functional-and-behavior-testing.jpg)
[photo source](https://images.unsplash.com/photo-1600492515568-8868f609511e?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1250&q=80){:target="_blank"}

## Functional Testing
### What is a functional test ?
Functional tests are one of these software testing approaches or test types such as (unit tests, integration tests, load tests, penetration tests, ...) all with one mission to test that the software is compliant whether with business specification, technical requirements or other quality and usability metrics. But functional tests focus on ensuring that the software functions behave as expected by the business specifications, these tests don't interact with source code such as unit tests, but mainly with the software features.
A functional test usually puts the system, the application or the software we want to test in an initial state where we provide the necessary elements to make the test executable such as storing a list of cars in the database, then we test the feature find a car for the period of (2nd march to 7th march), then we validate that the output matches the expected result.
### Why do we need to write functional tests?
We need to write functional test to validate the features from a user perspective, hence we validate the following:

 -  Feature is working as expected by the specifications
 -  Usability: checks whether the feature is easily usable, for example, a button is freely reachable on the page.
 -  Errors: when a subsystem is not responding, do we display an error message to the user to help him understand what's going on.

### Functional testing style
A common form that functional testing take is the Given-When-Then, this approach coming from the [BDD (Behaviour Driven Development)](#bdd-behavior-driven-development) defines the structure of many testing frameworks such as Cucumber that we will cover in our example later in this article.
The prime idea is to break down a scenario (test)  into three sections:

 - **Given**:  the given part defines the pre-conditions before challenging the system by executing or running a feature.
 - **When**: is do we want to do with the system, for example ( *when I book a car*)
 - **Then**: describes the expected result or output after the application or the software  behaves in to respond to your action.

To simplify the idea, let's write an example for a rental car website using the Cucumber Tool (Framework):

    Feature: User book a car
	    Scenario: User requests to book a car from 1st March to 7th March 2022
		     Given I select a car from the available cars for the period (1st March to 7th March 2022)
			    And I select GPS as an additional Option
			    And I select Full Insurance
			 When I book the car
			 Then I should receive a confirmation


### BDD: Behavior Driven Development
BDD combines the best practices of  **Test Driven Development** TDD, **Domain-driven Development** (**DDD**), and **Object Oriented Programming** (**OOPs**)
For an agile team, scoping a feature is a very important task, as the stakeholders are talking about the business requirements, the development team is more interested in the technical challenges, Here comes the **BDD** to provide a common language that allows efficient communication and feedback and then a perfect specification, development vision, and feature delivery.

BDD closes the gap between the business and the technical people by:

 - Encouraging collaboration across roles to build a shared understanding of the problem to be solved.
 - Working in a rapid and small iteration to promote the feedback and optimize the value delivery.
 - Producing documentation that is automatically checked against the software behavior.

There is a good chance that you're agile at your organization so you already plan your work in small increments of value like User Stories. In this case, BDD will help you to deliver your promises of agile on time. BDD does not replaces your processes but enhances them.

### BDD and Functional Testing
Let's focus on the word **Behaviour** so functional testing of behavior testing is these tests your write to check your system or the software you're building how behaves. Functional testing can also be called ***behavior testing***.

### Behaviour Testing in action
To illustrate all these abstract notions explained briefly in this article, let's write a small application and its behavior tests using **Kotlin** programming language and **Cucumber**

 - **Kotlin** is a JVM programming language, like Java, Scala, or Groovy
 - **Cucumber** is a testing tool that supports Behavior Driven Development
 - **Gherkin**  is a business readable language that helps you to describe business behavior without going into details of implementation

We will need the following to build this example:

 1.   [Java SE](https://www.oracle.com/technetwork/java/javase/downloads/index-jsp-138363.html)  (Java 9 and higher are not yet supported by Cucumber)
 2.   [Maven](https://maven.apache.org/index.html)  - version 3.3.1 or higher
 3.   [IntelliJ IDEA](https://www.jetbrains.com/idea/)  (which will be used in this tutorial)
    -   [IntelliJ IDEA Cucumber for Java plugin](https://plugins.jetbrains.com/plugin/7212-cucumber-for-java)
    -   [IntelliJ IDEA Kotlin plugin](https://plugins.jetbrains.com/plugin/6954-kotlin)


1. Clone the project from github

```shell
git clone https://github.com/reda-jaifar/hands-on-kotlin.git
cd sportair
```
 2. Open the project in IntelliJ IDEA:

	-   **File -> Open… -> (Select the pom.xml)**
	-   Select  **Open as Project**

3. Verify Cucumber installation

```shell
mvn test
```
Now our environment is ready, let's write some scenarios for the following application:

    SportAir is an application that indicates whether we
    can exercise outside or not based on the weather.

In Cucumber, an example is called a [scenario](https://cucumber.io/docs/gherkin/reference#example). Scenarios are defined in `.feature` files, which are stored in the directory (or a subdirectory).

Create an empty file called `src/test/resources/sportair/can_we_exercice_outtside.feature`  with the following content:

    Feature: Can we exercise outside?
          Everybody wants to know if we can exercise in the air

          Scenario: The weather is not convenient for exercising outside
            Given The temperature is 42 celsius
            When I ask whether I can exercise outside
            Then I should be told "Nope"

if you're using Intellij Idea Cucumber Plugin, you should see the keyword colored, below the meaning of each:

 - **Feature**: is a keyword that should be followed by the feature name, a good practice is to use the name of the file. The line that follows is a description that will be ignored by Cucumber execution parser.
   <br />**NB**:  We use a feature by file
 - **Scenario**: defines the name of a scenario, we can have as many scenarios as expected by a feature.
 - **Given, When, Then**: are the steps of the scenario. Refers to the definition [above](#functional-testing-style).
```shell
mvn test
 ```

```shell
The output should be something like the following:
 Given The temperature is 42                                  # StepDefs.The temperature is(int)
    When I ask whether I can exercise outside                    # StepDefs.I ask whether I can exercise outside()
    Then I should be told nope                                   # StepDefs.I should be told(String)

  Scenario: The weather is convenient for exercising outside # sportair/can_we_exercice_outside.feature:9
    Given The temperature is 24                              # StepDefs.The temperature is(int)
    When I ask whether I can exercise outside                # StepDefs.I ask whether I can exercise outside()
    Then I should be told of course                          # StepDefs.I should be told(String)

2 Scenarios (2 passed)
6 Steps (6 passed)
0m0.181s

Tests run: 2, Failures: 0, Errors: 0, Skipped: 0, Time elapsed: 0.403 sec

Results :

Tests run: 2, Failures: 0, Errors: 0, Skipped: 0
```

###  Behavior Driven Testing Benefits

 -  Helps document specification by the usage of non-technical language
 -  Focuses on how the system should behave from both user and developer perspective
 -  Gives high visibility of the system design
 -  Helps to make the software or the system meet the user need

The figure below illustrates the process of BDD and how it can help to write down behavior tests.

![BDD Process](/assets/img/figures/bdd-process.jpeg)

*This figure defines a step flow to help define and write down behavior tests*

----

* [Cucumber Documentation](https://cucumber.io/docs/cucumber/){:target="_blank"}
* [Testing & Domain Specific Language By Martin Fowler](https://martinfowler.com/bliki/GivenWhenThen.html){:target="_blank"}
* [Domain-driven design Book by Eric Evans](https://www.oreilly.com/library/view/domain-driven-design-tackling/0321125215/){:target="_blank"}

