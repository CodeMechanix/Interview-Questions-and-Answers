### Question
Difference between Spring MVC and Spring Boot?

I have just started learning Spring. In my next step, I would like to develop bigger web applications.
Now I am wondering if I should start with Spring Boot or Spring MVC. I have already read some stuff, but it is confusing because both look similar.
So what are the differences between the two?

---------------

### Answer
Spring MVC is a sub-project of the Spring Framework, targeting design and development of applications that use the MVC (Model-View-Controller) pattern. Spring MVC is designed to integrate fully and completely with the Spring Framework and transitively, most other sub-projects.

In a simple term it can be stated as:

> Spring boot = Spring MVC + Auto Configuration(Don't need to write spring.xml file for configurations) + Server(You can have embedded Tomcat, Netty, Jetty server).

And Spring Boot is an Opinionated framework, so its build taking in consideration for fast development, less time need for configuration and have a very good community support.

-----------
Using spring boot you will no need to build configuration. This will have done automatically when you create project.

If you use spring MVC you need to build configuration yourself. It is more complicated, but it is crucial.

----------

Think this way:

Spring MVC is a web based framework to implement the MVC architecture.

Spring Boot is a tool oriented to the programmer. Programmer must focus on programming and tool must focus on configurations. So we don't need to wast our time configuring a bunch of xml to make a simple 'Hello world'.
