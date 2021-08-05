---
layout: post
title:  "DevOps: Strengthen your digital transformation"
date:   2021-07-10 10:49:31 +0100
categories: stories
thumbnail_image: /assets/img/posts/devops-strengthen-your-digital-transformation.jpeg
---
![author](/assets/img/posts/devops-strengthen-your-digital-transformation.jpeg)
[photo source](https://www.sdxcentral.com/cdn-cgi/image/w=748,h=399,fit=scale-down,f=auto,q=85/https://www.sdxcentral.com/wp-content/uploads/2018/10/Cloudera-Hortonworks-Merge-Their-Big-Data-Efforts.jpg){:target="_blank"}
<style>
* {
  box-sizing: border-box;
}

body {
  font-family: Arial, Helvetica, sans-serif;
}

p.card-content {
font-size: 13px;
}
/* Float four columns side by side */
.column {
  float: left;
  width: 25%;
  padding: 0 10px;
}

/* Remove extra left and right margins, due to padding */
.row {margin: 0 -5px;}

/* Clear floats after the columns */
.row:after {
  content: "";
  display: table;
  clear: both;
}

/* Responsive columns */
@media screen and (max-width: 600px) {
  .column {
    width: 100%;
    display: block;
    margin-bottom: 20px;
  }
}

/* Style the counter cards */
.card {
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
  padding: 16px;
  text-align: center;
  background-color: lightblue;
}
</style>

Nowadays the processes used to create software have been considerably evolved from manual and human interaction to test,
build and deploy an application to a fully automated process relying on new practices and tools that help teams to 
deliver an update to production in few minutes or even seconds.
If your organization or team still using the old methods and have the willingness to take a step toward these useful
and helpful DevOps practices, there are some notions to consider while taking the way.

# DevOps: Development and Operations fusion
DevOps aims at merging or combining the software development and IT operations to accelerate software delivery while ensuring high quality and secure systems.
with the adoption of agility, a team could respond to customer requirements rapidly without suspending the production environment. I would like to sum up these concepts as follow:

   - Development and operations teams are merged into one single team where all members contributing to make
     the app ready to use, from dev, and test to deployment.
   - Product Owner and other functional roles are concerned by DevOps practices, they decide and act from feature
     development to application production deployment. ​

Before detailing the concepts and practices of DevOps, let's share some of the key benefits of either a company or an open community
developing a product can gain.

<div class="row">
  <div class="column">
    <div class="card">
      <h3>Speed</h3>
      <p class="card-content">Increase your velocity for faster innovation and market-changing responding by releasing updates quickly</p>
    </div>
  </div>

  <div class="column">
    <div class="card">
      <h3>Delivery</h3>
      <p class="card-content">Reducing the delivery time to provide customer with new features and fixing bugs quickly</p>
    </div>
  </div>
  
  <div class="column">
    <div class="card">
      <h3>Security</h3>
      <p class="card-content">
      Respond and deliver quicker without losing control on quality and compliance, by including automated quality and security checking
      </p>
    </div>
  </div>
  
  <div class="column">
    <div class="card">
      <h3>Reliability</h3>
      <p class="card-content">Manage your development, test and production environment in a managed manner to test that every changes or updates is functional so the end user is always provided with a reliable product </p>
    </div>
  </div>
</div>

## DevOps practices
# Continuous Integration
Today chances that software is writing by more than one person are higher contrary to the shining start of the Linux story who was
created first by Linus Torvalds as a personal project. To merge code writing by different members we use the continuous integration
which is a simple idea about committing code frequently to a shared central repository on a server, then an automated conflicts resolving,
test and build are triggered, this practice keeps developers focused on writing code for new features rather than debugging code merging issues
Today the market is full of different products that we can rely on for managing source code and continuous integration, the most famous
are:

- [Github](https://github.com/){:target="_blank"}
- [Gitlab](https://gitlab.com){:target="_blank"}
- [AWS CodeCommit](https://aws.amazon.com/codecommit/){:target="_blank"}
- [BitBucket](https://bitbucket.org/){:target="_blank"}
- [Google Cloud Source Repositories](https://cloud.google.com/source-repositories){:target="_blank"}

# Continuous Delivery
Time to market is a key factor many businesses usually is taking into consideration, they were always interested in how to
test an idea ASAP and put that product or service in customer's hand and gather a quick feedback. To collect a reliable
feedback and analysis how the user interact with the software there is a need to provide it in a real production environment.
Continuous Delivery also known as CD respond to this requirement and more through the adoption of a set of practices and tools
that they will help your organization to automatically build, test and deploy a new version or small change to production
rapidly.
Find below some of the most used CI/CD platforms:

- [Github Actions](https://github.com/features/actions){:target="_blank"}
- [Gitlab CI/CD](https://docs.gitlab.com/ee/ci/){:target="_blank"}
- [AWS CodePipelines](https://aws.amazon.com/codepipeline/){:target="_blank"}
- [CircleCi](https://circleci.com/){:target="_blank"}
- [Google Cloud Source Repositories](https://cloud.google.com/source-repositories){:target="_blank"}

## More than CI/CD
While the continuous integration and delivery remain the most known practices of DevOps, There are others not less important
and should be implemented and adopted to have a standard compliant Workflow as illustrated in the following drawing:
![DevOps Workflow](/assets/img/posts/devops-workflow.jpeg)

Once a change or new feature has been deployed, we need to operate on, to configure for example an endpoints or enable
that feature using a distributed configuration system. Then we need to monitor so see how the a deployment impacts the 
user experience and performances. Automated the monitoring and capturing logs from the application, analyzing them in order
to ensure a 24/7 service availability.

The following cards describe some necessary practices to consider too while promoting a DevOps culture and deploying the
tools.
 
<div class="row">
  <div class="column">
    <div class="card">
      <h4>Microservices</h4>
      <p class="card-content">Microservice architecture aims at decomposing a complex application into modules developed and understood by different people</p>
    </div>
  </div>

  <div class="column">
    <div class="card">
      <h4>Infrastructure as Code</h4>
      <p class="card-content">is a practice in which infrastructure is provisioned and managed using code and software development techniques</p>
    </div>
  </div>
  
  <div class="column">
    <div class="card">
      <h4>Monitoring and Logging</h4>
      <p class="card-content">
      Applications logs and data are collected and analyzed, and infrastructure metrics are monitored to trigger scaling up/down
      or respond to an unexpected event.
      </p>
    </div>
  </div>
  
  <div class="column">
    <div class="card">
      <h4>Communication</h4>
      <p class="card-content">Merging development and operations efforts requires a good and seamless communication and collaboration, we can rely  on different channels like chat apps and tracking-systems</p>
   </div>
  </div>
</div>

# Example: How microservices and DevOps can be implemented together to transform an application?
With the adoption of microservices architecture, your pipeline could take another structure, in the following example
we illustrate an old and a modern pipeline for an hotel booking application:
__Booking Application__ is an application that cover mainly 3 modules as follow:

![Hotel Booking Application](/assets/docs/hotel-booking-app-pipleline-v1.svg)
*The large Hotel Booking App team commits their changes to a single source code repository. The path from code to production is long and onerous and involves manual intervention*

Now let's discover how ce can transform our hotel booking application to make it easily extensible, maintainable and continuously
updated. We will decompose the monolithic application into small loosely coupled services, and put in place a modern pipeline
to help us respond rapidly to new requested changes and deliver quicker new versions. The figure below demonstrate the new application
architecture and pipeline structures:

![Hotel Booking Application](/assets/docs/hotel-booking-app-pipleline-v2.svg)
*The microservices-based application consists of a set of small, decoupled services, developed, tested and deployed independently thanks to a fully automated CI/CD*

---


**NOTE**
In the above figure, we mention gitlab CI/CD as our continuous integration and deployment platform.We can use
any other combination of DevOps tools from the ones listed in previous paragraphs. 

---

Finally, I would like to share my thoughts about DevOps, First of all is all about a culture, a change that the organization should be prepared for, I’m think about people within our teams who are comfortable with old processes to deliver software, we should walk with them side by side during the promotion phase to help them understand and believe in the benefits they can gain with these new ways of creating software.

The second point is about the tools, today there are plenty of DevOps tools we can choose from, In my point of view having a whole one platform that provides implementations for major needed tools is extremely recommended such as CI/CD, tracking systems, code source repository, etc…

The last point is about the word "continuous" because once we put in place these DevOps tools and spread the practices we think that the job is done but is all about continuous improvement and surely new issues will be faced and we need to be prepared to analyze and solve them again, this what engineering is about.

* [AWS DevOps](https://aws.amazon.com/devops/what-is-devops/){:target="_blank"}
* [Microservices Patterns by Chris Richardson](https://www.manning.com/books/microservices-patterns){:target="_blank"}
