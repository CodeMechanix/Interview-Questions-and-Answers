### Question
What is AOP?

### Answer

The application is generally developed with multiple layers. A typical Java application has the following layers:

1. Web Layer: It exposes the services using the REST or web application.
2. Business Layer: It implements the business logic of an application.
3. Data Layer: It implements the persistence logic of the application.

The responsibility of each layer is different, but there are a few common aspects that apply to all layers are Logging, Security, validation, caching, etc. These common aspects are called cross-cutting concerns.

If we implement these concerns in each layer separately, the code becomes more difficult to maintain. To overcome this problem, Aspect-Oriented Programming (AOP) provides a solution to implement cross-cutting concerns.

- Implement the cross-cutting concern as an aspect.
- Define pointcuts to indicate where the aspect has to be applied.

It ensures that the cross-cutting concerns are defined in one cohesive code component.

#### AOP
AOP (Aspect-Oriented Programming) is a programming pattern that increases modularity by allowing the separation of the cross-cutting concern. These cross-cutting concerns are different from the main business logic. We can add additional behavior to existing code without modification of the code itself.

Spring's AOP framework helps us to implement these cross-cutting concerns.

Using AOP, we define common functionality in one place. We are free to define how and where this functionality is applied without modifying the class to which we are applying the new feature. The cross-cutting concern can now be modularized into special classes, called aspect.

There are two benefits of aspects:
- First, the logic for each concern is now in one place instead of scattered all over the codebase.
- Second, the business modules only contain code for their primary concern. The secondary concern has been moved to the aspect.

The aspects have the responsibility that is to be implemented, called advice. We can implement an aspect's functionality into a program at one or more join points.

Benefits of AOP
- It is implemented in pure Java.
- There is no requirement for a special compilation process.
- It supports only method execution Join points.
- Only run time weaving is available.
- Two types of AOP proxy is available: JDK dynamic proxy and CGLIB proxy.

The cross-cutting concern is a concern that we want to implement in multiple places in an application. It affects the entire application.

AOP Terminology
- Aspect: An aspect is a module that encapsulates advice and pointcuts and provides cross-cutting An application can have any number of aspects. We can implement an aspect using regular class annotated with @Aspect annotation.
- Pointcut: A pointcut is an expression that selects one or more join points where advice is executed. We can define pointcuts using expressions or patterns. It uses different kinds of expressions that matched with the join points. In Spring Framework, AspectJ pointcut expression language is used.
- Join point: A join point is a point in the application where we apply an AOP aspect. Or it is a specific execution instance of an advice. In AOP, join point can be a method execution, exception handling, changing object variable value, etc.
- Advice: The advice is an action that we take either before or after the method execution. The action is a piece of code that invokes during the program execution. There are five types of advices in the Spring AOP framework: before, after, after-returning, after-throwing, and around advice. Advices are taken for a particular join point. We will discuss these advices further in this section.
- Target object: An object on which advices are applied, is called the target object. Target objects are always a proxied It means a subclass is created at run time in which the target method is overridden, and advices are included based on their configuration.
- Weaving: It is a process of linking aspects with other application types. We can perform weaving at run time, load time, and compile time.
- Proxy: It is an object that is created after applying advice to a target object is called proxy. The Spring AOP implements the JDK dynamic proxy to create the proxy classes with target classes and advice invocations. These are called AOP proxy classes.

There are five types of AOP advices are as follows:

1. Before Advice: An advice that executes before a join point, is called before advice. We use @Before annotation to mark an advice as Before advice.
2. After Advice: An advice that executes after a join point, is called after advice. We use @After annotation to mark an advice as After advice.
3. Around Advice: An advice that executes before and after of a join point, is called around advice.
4. After Throwing Advice: An advice that executes when a join point throws an exception.
5. After Returning Advice: An advice that executes when a method executes successfully.

Before implementing the AOP in an application, we are required to add Spring AOP dependency in the pom.xml file.

```text
<dependency>  
<groupId>org.springframework.boot</groupId>  
<artifactId>spring-boot-starter-aop</artifactId>  
<version>2.2.2.RELEASE</version>  
</dependency> 
```

See Code: 
1. [Spring Boot AOP Before Advice](https://www.javatpoint.com/spring-boot-aop-before-advice)
2. [Spring Boot AOP After Advice](https://www.javatpoint.com/spring-boot-aop-after-advice)
3. [Spring Boot AOP Around Advice](https://www.javatpoint.com/spring-boot-aop-around-advice)
4. [Spring Boot AOP After Returning Advice](https://www.javatpoint.com/spring-boot-aop-after-returning-advice)
5. [Spring Boot AOP After Throwing Advice](https://www.javatpoint.com/spring-boot-aop-after-throwing-advice)

