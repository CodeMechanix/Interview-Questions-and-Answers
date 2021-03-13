### Java OOPS interview questions and answers

> What is Abstraction?

Abstraction is a concept of showing only important information and hiding its implementation.

For example:

> > When you see a car, you know it is running but how it's running internally, you may be not aware of it.

> > Another way, it shows only essential things to the user and hides the internal details, for example, sending SMS where you type the text and send the message. You don't know the internal processing about the message delivery.

This is Abstraction. You just expose required details.

There are two ways to achieve abstraction in java

1. Abstract class (0 to 100%)
2. Interface (100%)

- Abstract class in Java:

A class which is declared as abstract is known as an abstract class. It can have abstract and non-abstract methods. It
needs to be extended and its method implemented. It cannot be instantiated.

Points to Remember

1. An abstract class must be declared with an abstract keyword.
2. It can have abstract and non-abstract methods.
3. It cannot be instantiated.
4. It can have constructors and static methods also.
5. It can have final methods which will force the subclass not to change the body of the method.

* Example of abstract class

```text
abstract class A{}  
```

* Abstract Method in Java

```text
abstract void printStatus();//no method body and abstract  
```

> > > Example of Abstract class that has an abstract method

```java
abstract class Bike {
    abstract void run();
}

class Honda extends Bike {
    void run() {
        System.out.println("Running safely");
    }

    public static void main(String args[]) {
        Bike obj = new Honda();
        obj.run(); // Running safely
    }
}  
```

> > > Abstract class having constructor, data member and methods

```java
//Example of an abstract class that has abstract and non-abstract methods  
abstract class Bike {
    Bike() {
        System.out.println("Bike is created");
    }

    abstract void run();

    void changeGear() {
        System.out.println("Gear changed");
    }
}

//Creating a Child class which inherits Abstract class  
class Honda extends Bike {
    void run() {
        System.out.println("Running safely..");
    }
}

//Creating a Test class which calls abstract and non-abstract methods  
class TestAbstraction2 {
    public static void main(String args[]) {
        Bike obj = new Honda();
        obj.run();  
      /*
           Bike is created
           Running safely..
       */
        obj.changeGear();
        // Gear changed
    }
}  
```

> Interface in Java

An interface in Java is a blueprint of a class. It has static constants and abstract methods.

The interface in Java is a mechanism to achieve abstraction. There can be only abstract methods in the Java interface,
not method body. It is used to achieve abstraction and multiple inheritance in Java.

In other words, you can say that interfaces can have abstract methods and variables. It cannot have a method body.

Java Interface also represents the IS-A relationship.

- There are mainly three reasons to use interface. They are given below.

1. It is used to achieve abstraction.
2. By interface, we can support the functionality of multiple inheritance.
3. It can be used to achieve loose coupling.

An interface is declared by using the interface keyword. It provides total abstraction; means all the methods in an
interface are declared with the empty body, and all the fields are public, static and final by default. A class that
implements an interface must implement all the methods declared in the interface.

```java
interface<interface_name>{
        // declare constant fields  
        // declare methods that abstract   
        // by default.  
        }  
```

> Java Interface Example

```java
interface printable {
    void print();
}

class A6 implements printable {
    public void print() {
        System.out.println("Hello");
    }

    public static void main(String args[]) {
        A6 obj = new A6();
        obj.print();
    }
}  
```

> Multiple inheritance in Java by interface

```java
interface Printable {
    void print();
}

interface Showable {
    void show();
}

class A7 implements Printable, Showable {
    public void print() {
        System.out.println("Hello");
    }

    public void show() {
        System.out.println("Welcome");
    }

    public static void main(String args[]) {
        A7 obj = new A7();
        obj.print();
        obj.show();
    }
}  
```

Multiple inheritance is not supported in the case of class because of ambiguity. However, it is supported in case of an
interface because there is no ambiguity.

> Interface inheritance

```java
interface Printable {
    void print();
}

interface Showable extends Printable {
    void show();
}

class TestInterface implements Showable {
    public void print() {
        System.out.println("Hello");
    }

    public void show() {
        System.out.println("Welcome");
    }

    public static void main(String args[]) {
        TestInterface obj = new TestInterface();
        obj.print();
        obj.show();
    }
}  
```

> Java 8 Default Method in Interface

```java
interface Drawable {
    void draw();

    default void msg() {
        System.out.println("default method");
    }
}

class Rectangle implements Drawable {
    public void draw() {
        System.out.println("drawing rectangle");
    }
}

class TestInterfaceDefault {
    public static void main(String args[]) {
        Drawable d = new Rectangle();
        d.draw();
        d.msg();
    }
}  
/*
        Output
        drawing rectangle
        default method
 */
```

> Difference between abstract class and interface

Abstract class Interface

1) Abstract class can have abstract and non-abstract methods. Interface can have only abstract methods. Since Java 8, it
   can have default and static methods also.
2) Abstract class doesn't support multiple inheritance. Interface supports multiple inheritance.
3) Abstract class can have final, non-final, static and non-static variables. Interface has only static and final
   variables.
4) Abstract class can provide the implementation of interface. Interface can't provide the implementation of abstract
   class.
5) The abstract keyword is used to declare abstract class. The interface keyword is used to declare interface.
6) An abstract class can extend another Java class and implement multiple Java interfaces. An interface can extend
   another Java interface only.
7) An abstract class can be extended using keyword "extends". An interface can be implemented using keyword "implements"
   .
8) A Java abstract class can have class members like private, protected, etc. Members of a Java interface are public by
   default.
9) Example:
   ```java
   public abstract class Shape{
   public abstract void draw();
   }
   ```   
   Example:
   ```java
   public interface Drawable{
   void draw();
   }
   ```