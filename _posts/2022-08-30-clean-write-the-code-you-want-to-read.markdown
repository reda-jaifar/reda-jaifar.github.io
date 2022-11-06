---
layout: post
title:  "Clean code: Write The Code You Want To Read (Part 1)"
date:   2022-08-30 21:06:46 +0100
categories: stories
thumbnail_image: /assets/img/posts/clean-code-write-the-code-you-want-to-read.jpg
---
![author](/assets/img/posts/clean-code-write-the-code-you-want-to-read.jpg)
[photo source](https://unsplash.com/photos/FTNGfpYCpGM){:target="_blank"}

## Clean Code!
### Why should I care?
We, software engineers almost spent more time reading code than writing new lines, how many times do we complain about someone else's code? Many factors can give us an idea about
the quality of code and how much the writer cares about it. If you dislike reading bad code, you already made your first step toward writing good code if you care about
your heritage.
There are many good reasons to care about writing clean code, adding the artistic layer to your code is an inspiring reason for me to learn and apply the clean code rules and principles.

### What clean code brings to me?
Clean code is what makes us professional programmers, someone with high-level ethics who cares about the present and the future of his code, he believes that lines of code
can live for long and can be enhanced by others with ease and passion. Like a book author what makes him happy is how readers enjoy turning the pages of his book one after the other without realizing the time elapsed.

### Clean code is about philosophy!
Clean code makes us more than a programmer, it helps us develop a good vision of the software we are building, caring about its growth, evolutionary, and enhancement. Clean code makes us a thinker about
maintainability, design, and the ability of the software to cope with changes quickly and easily.
Code is written to live but also to change and evolve.

### We are authors
Yes, we programmers are authors, that said, we have readers, Indeed we are responsible for communicating well with readers. The next time we write a line of code, we'll remember
we are authors, writing for readers who will judge our effort.

## What clean code covers?

### Naming
As a programmer the first step of writing code is choosing names, for variables, functions, classes, packages and source code files.
While this seems easy and instinctive, choosing good names takes time but saves more than it takes.

Let's look at the following code snipped:
```shell
 d = Date.now();
```
The name "d" above has nothing to reveal, even tough it is a date object, but we cannot know the intention of usage, either its start date or end date.
Note that even naming it startDate doesn't give it any sense, because we need to know as a reader what is the context of the start date.
Hers is a suggestion for this example:
```shell
taskStartDate = Date.now();
```
#### Abbreviation
Abbreviation Is one of the most common mistakes concerning variable naming, as a programmer can you guess what this variable name below means?
```shell
msg
```
Can you know that msg may mean "message" or "most scored goal"? Personally, I don't want to spend time exploring many lines before
or after this one to understand the context of this variable in case I need to make a change. The rule is to avoid any disinformation.

#### Distinction
Another issue with naming is the number-series such as (variable1, variable2), consider the following function:
````java
public static void duplicateString(char a1[], char a2[]){
        ...
        }
````
is it not more readable if we use "source" and "destination" as the names of the two arguments? I think yes, it is.

Adding noise words is another problem that impacts the cleanness of the code, you may want  to specify that a variable is 
a String, so you name it: __"emailContentString"__, Here the "String" is just redundant as is not part of the name but the type
which has nothing to do with the meaning of the variable.

#### Word Sounding
As a programmer, there is a good chance that while we are writing code, our brain is pronouncing the text we type. when we cut the connection
between our brain and the activity of writing, we usually type variable names that could be difficult to pronounce, and the consequences
are multiple: other developers won't be able to retain them easily and these names will be demanding to discuss with the business analysts.
While English is the most used natural language used to write code, using other languages such as  French or Italian, apply the same rules regarding
how easily the variables, functions, or classes names are pronounceable.

#### Are names accessible?
Each time I take over developing a new feature or fixing a bug that requires modifying a source code that not has been writing by me,
I start by searching some keywords that I got from the context of the domain system. For Example when I was asked to fix
a UI bug in a web application developed using ReactJS then I was trying to find the matching component in the source code, but it was not as
easy as expected and I spent 30 minutes before finding the component named with a number prefix: 1CounterComponent. This is why
choosing names that are straightforward to find is a very useful rule to follow.


#### Coding Conventions
Every programming language provides coding conventions regarding variables, functions, classes, and naming source code files. While
the naming took a good part of these conventions, they also cover indentation, comments, declaration order, etc ...
I don't hesitate to refer to these conventions. But during my modest experience, I came across some coding conventions
from specific programming languages applied to another one. This is strongly discouraged or prohibited by the teams themselves.

#### Technical Vs Business Names
We write code to build software that will be solving a problem, For example: coding an application that computes taxes.
Trying to be a good programmer implies differentiating technical things from business-related ones. whenever you code
a technical concept don't try to use mainly a domain name, For example: declaring a variable that holds an instance of the
HTTP client could have the following name: __httpClient__, but if we try to include the business-related usage we can name it:
__taxesRulesHttpClient__ as you can see in this case the domain doesn't bring any help instead is just making a technical
thing harder.

#### A last note
Writing clean code requires a piece of cultural knowledge and good descriptive, communication, and writing skills, we can develop
these skills by learning from communication experts either by reading books or taking courses on how to write, synthesis, and
order ideas. Also evolving on the natural language we use to code. For example, if we write code in English, it will be helpful
to learn more words, synonyms, sentences, etc...

So far I wanted to pay your attention to the importance of clean code, and how can impact the software's quality and maintenance,
We covered mainly the naming concept in this part. Other articles will follow to cover other aspects concerned by clean code.

----

* [The Clean Code Blog](https://blog.cleancoder.com/){:target="_blank"}
* [Clean Code: A Handbook of Agile Software Craftsmanship by Robert C. Martin](https://www.oreilly.com/library/view/clean-code-a/9780136083238/){:target="_blank"}
* [10 steps to clean code](https://www.pluralsight.com/blog/software-development/10-steps-to-clean-code){:target="_blank"}
* [Kotlin coding conventions](https://kotlinlang.org/docs/coding-conventions.html){:target="_blank"}

