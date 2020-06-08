---
title: "A Step by Step guide to a Spring Boot Microservices workshop for #WWCode — Part 2"
date: 2018-01-14T08:00:00+08:00
draft: false
---

In the previous section, we looked at cloning the skeleton from my github repo (or downloading from Spring Initializr). In this section we will look at building our first Restful endpoint. We will also look at using Properties.

Please note: You can also follow through these exercises with the full workshop on my github repo — https://github.com/pkamath2/GOT-heroes-full


### Exercise 3
While writing any web based application, we need to provide a context location (where the application is deployed on a server) and the port on which it is deployed.

#### **Step 1**
Update the application.properties file (found under GOT-heroes/src/resources folder) with two properties -

{{<highlight bash>}}
* server.context-path=/wwcode
* server.port=${PORT:9000}
{{</highlight>}}

This tells spring boot that we would need to serve all http end points within this application through a base context root of “/wwcode”. And the port to be used will be 9000 i.e. when you access the application the url will be (atleast) http://localhost:9000/wwcode

Note that the ${PORT:9000} — this is part of SpEL or Spring expression language, which is a powerful way of injecting properties in Spring. This is useful especially when you deploy applications and you dont know which port you will be using eventually. Runtime environments (like Heroku) can inject the next available port for Spring Boot to use this way.


#### **Step 2**
Create a package called “controller” under “org.wwcode.springboot.GOTheroes”. Then create a class called “GOTHeroesController”. The package and class looks something like this —

 {{<figure src="/images/blog/spring-boot-part-2/intellij_setup.png" caption="org.wwcode.springboot.GOTheroes.GOTHeroesController">}}


#### **Step 3**
Lets create some Rest end points!

* Annotate GOTHeroesController with ‘@RestController’. This tells Spring boot that this class defines Restful end points.
* Add a ‘@RequestMapping(path=”/GOT”)’. This would tell Spring all end points in this class can be sourced at location “http://localhost:9000/wwcode/GOT”
* Lets create a POJO (or Business object/BO if you would like to use that terminology) called “GOTHero” under the package “org.wwcode.springboot.bo”. This java bean should hold properties of a Game Of Thrones hero! Define variables like name, title, allegiance, id and image location. Generate respective getters/setters.

 {{<figure src="/images/blog/spring-boot-part-2/getter_setter.png">}}

* Go back to the GOTHeroesController class and create a method called “public List<GOTHero> heroes(){}”. This method will need to return an empty ArrayList<GOTHero> (For now. We will update this method later)
* Annotate this method with “@RequestMapping” and “@ResponseBody”

{{<figure src="/images/blog/spring-boot-part-2/request_mapping.png">}}

* Restart the “GOTHeroesApplication” and hit http://localhost:9000/wwcode/GOT/heroes on your browser. You should see an empty list displayed.

Congratulations on your first Restful end point!

* Lets explore how we can provide request parameters and path variables. Create another method (like heroes) — lets call it “public GOTHero hero(int id){}”. This method should return a single hero based on the id passed.
* Annotate the method with “@PathVariable” and “@RequestParam” annotations.

{{<figure src="/images/blog/spring-boot-part-2/path_variable.png">}}

The “@PathVariable” annotation helps inject any dynamic variable on the path into the id method parameter. The “@RequestParam” injects any additional parameters sent via the url as method parameter.

* Restart the GOTHeroesApplication again and hit the browser url — http://localhost:9000/wwcode/GOT/hero/1?param=xyz. You should be able to see “id = [1], param = [xyz]” printed on your console.

This completes our exercise on Rest Controller. Our next exercise is on injecting an in-memory DB.

Next part: [A Step by Step guide to a Spring Boot Microservices workshop for #WWCode — Part 3]({{<ref "spring-boot-part-3.md">}})