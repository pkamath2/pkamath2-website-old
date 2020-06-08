---
title: "A Step by Step guide to a Spring Boot Microservices workshop for #WWCode — Part 1"
date: 2018-01-14T08:00:00+08:00
draft: false
---

I hosted a workshop on Spring Boot on 10th January for my Women Who Code Singapore network. We all collectively built a “Game of Thrones Heroes” webpage, powered by Microservices using Spring Boot. It had all the frills associated with an embedded server application — Restful end points in both JSON as well as XML, various configuration properties, an in memory (or file) DB setup, in memory spring security & a deployment to Heroku.

We split the workshop into 8 exercises. Though we could not finish all the modules, the audience was engaged and eager to learn more. I thought I should write up a step by step guide to the workshop, so that everyone can follow this through at home as well.
We asked the participants to install the following pre-requisites before the workshop started: 

* Java 8
* Create a github account & install git (CLI or Desktop)
* Maven 3.3+
* IntelliJ IDEA or Eclipse
* Google Chrome with Postman extension (optionally we could use Chrome developer tools)
* Create a Heroku account & install heroku CLI

The slides for the event can be found here — [https://github.com/pkamath2/GOT-heroes-full/raw/master/January-CodingWithJava-SpringBoot-PDF.pdf](https://github.com/pkamath2/GOT-heroes-full/raw/master/January-CodingWithJava-SpringBoot-PDF.pdf)

### Exercise 1

I love Spring Boot because it comes with these default “opinionated” starter dependencies, which are production worthy, and can be easily overridden if your team decides to use something else. For instance, the default embedded server is tomcat, which can be easily overridden to use Jetty or undertow. Or like the default connection pooling for database connections is dbcp2, and you can use Hikari if you would like to.

In this exercise we will create an initial Spring Boot skeleton, which can be further updated to create our app. For this workshop, you can create the skeleton two ways (choose any one way) —

* **Option 1**: Go to https://start.spring.io/ and update the fields as shown in the image and click “Generate Project”.

    {{<figure src="/images/blog/spring-boot-part-1/initialiser.png" caption="Go to https://start.spring.io. In the dependencies section search and “Web”, “Security”, “JPA” & “H2” individually and select the suggested dependencies.">}}

* **Option 2**: Clone the skeleton project I created on github at https://github.com/pkamath2/GOT-heroes. Execute below via command line -
    {{<highlight bash>}}$ git clone https://github.com/pkamath2/GOT-heroes{{</highlight>}}

**Kindly note:** For this workshop, I would prefer if you would clone the starter from my github repo (option 2), as I have updated the pom.xml with few more dependencies we will be using through the workshop. I have also commented out Spring Security for the time being. We will be looking at Spring Security basics during Exercise 7.

**Tip:** Which ever option you choose, clone another project from my github repo — https://github.com/pkamath2/GOT-heroes-full to a folder on your local machine. This is the full solution to the workshop we will be going through during all the exercises.


---
### Exercise 2

In this exercise, we will import the downloaded zip file (**option 1** from above) or the cloned project from my github repo (**option 2**).

To keep things simple, I will be using the cloned repo from **option 2**. Import the project into IntelliJ IDEA.

{{<figure src="/images/blog/spring-boot-part-1/intellij_setup.png" caption="The full workshop imported on my IntelliJ IDEA">}} 

In the ‘Maven Projects’ view, select package and run. If everything is installed correctly (Java 8, Maven 3.3+) running mvn package should create a target folder with a “GOT-heroes-0.0.1-SNAPSHOT.jar” in it.

Now that we have built the “Uber Jar” for a Spring Boot Application, lets try to run it. Open the GotHeroesApplication.java in your IDE, this class has a main method which you should run/execute. This starts the application on your local machine using some Spring Boot starter defaults. We are using tomcat as our embedded server.

Alternatively, you can run the application on a Terminal/Command prompt. Just type “java -jar target/GOT-heroes-0.0.1-SNAPSHOT.jar” at your project folder. This should run and start the embedded server as well.

Lets now proceed to Exercise 3 where we will write our first Restful endpoint.

Next part: [A Step by Step guide to a Spring Boot Microservices workshop for #WWCode — Part 2]({{<ref "spring-boot-part-2.md">}})