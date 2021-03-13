### Question

What is Dependency Injection and Inversion of Control in Spring Framework?

### Answer

In simple terms..

IOC(Inversion of Control) is a concept that means: Instead of creating objects with the new operator,let the container
do it for you.

DI(Dependency injection) is way to inject the dependency of a framework component by the following ways of spring:

1. Contructor injection
2. Setter/Getter injection
3. field injection

-----------------------
IOC is technique where you let someone else to create the object for you. And the someone else in case of spring is IOC
container.

Dependency Injection is a technique where one object supplies the dependency of another object.

-----------------------


Inversion of control- It means giving the control of creating and instantiating the spring beans to the Spring IOC
container and the only work the developer does is configuring the beans in the spring xml file.

Dependency injection-

Consider a class Employee

```java
class Employee {
    private int id;
    private String name;
    private Address address;

    Employee() {
        id = 10;
        name = "name";
        address = new Address();
    }
}
```
and consider class Address
```java
class Address {
   private String street;
   private String city;

   Address() {
     street="test";
     city="test1";

  }
}
```
In the above code the address class values will be set only when the Employee class is instantiated, which is dependency of Address class on Employee class. And spring solves this problem using Dependency Injection concept by providing two ways to inject this dependency.

1. Setter injection

Setter method in Employee class which takes a reference of Address class
```java
public void setAddress(Address addr) {
    this.address = addr;
}
```
2. Constructor injection 

Constructor in Employee class which accepts Address

```java
Employee(Address addr) {
      this.address = addr;
}
```
In this way the Address class values can be set independently using either setter/constructor injection.
