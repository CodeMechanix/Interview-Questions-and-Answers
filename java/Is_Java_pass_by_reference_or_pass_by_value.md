### Question

Is Java “pass-by-reference” or “pass-by-value”?

-----------

### Answer

Java is always pass-by-value. Java always passes arguments by value, NOT by reference.

It goes like this:

```java
public class Main {

    public static void main(String[] args) {
        Foo f = new Foo("f");
        changeReference(f);// f // It won't change the reference!
        modifyReference(f);// c // It will modify the object that the reference variable "f" refers to!
    }

    public static void changeReference(Foo a) {
        Foo b = new Foo("b");
        a = b;
    }

    public static void modifyReference(Foo c) {
        c.setAttribute("c");
    }

}
```

I will explain this in steps:

1. Declaring a reference named f of type Foo and assign it a new object of type Foo with an attribute "f".

> Foo f = new Foo("f");

2. From the method side, a reference of type Foo with a name a is declared and it's initially assigned null.

> public static void changeReference(Foo a)

3. As you call the method changeReference, the reference a will be assigned the object which is passed as an argument.

> changeReference(f);

4. Declaring a reference named b of type Foo and assign it a new object of type Foo with an attribute "b".

> Foo b = new Foo("b");

5. a = b makes a new assignment to the reference a, not f, of the object whose attribute is "b".

6. As you call modifyReference(Foo c) method, a reference c is created and assigned the object with attribute "f".

7. c.setAttribute("c"); will change the attribute of the object that reference c points to it, and it's the same object
   that reference f points to it.

I hope you understand now how passing objects as arguments works in Java :)

> Java passes references by value. So you can't change the reference that gets passed in.

Link: [Click Here](https://stackoverflow.com/questions/40480/is-java-pass-by-reference-or-pass-by-value?rq=1)

------------------

```java
public class Test {
    public static void main(String[] args) {
        Integer a = new Integer(2);
        Integer b = new Integer(3);
        System.out.println("Before: a = " + a + ", b = " + b); // Before: a = 2, b = 3
        swap(a, b);
        System.out.println("After: a = " + a + ", b = " + b); // After: a = 2, b = 3
    }

    public static void swap(Integer iA, Integer iB) {
        Integer tmp = iA;
        iA = iB;
        iB = tmp;
        System.out.println("Local Scope: a = " + iA + ", b = " + iB); // Local Scope: a = 3, b = 2
    }
}
```
This happens because iA and iB are new local reference variables that have the same value of the passed references (they point to a and b respectively). So, trying to change the references of iA or iB will only change in the local scope and not outside of this method.

------------

First, we should understand what is meant by pass by value or pass by reference.

Pass by Value: The method parameter values are copied to another variable and then the copied object is passed, that’s why it’s called pass by value.

Pass by Reference: An alias or reference to the actual parameter is passed to the method, that’s why it’s called pass by reference.

Let’s say we have a class Balloon like below.
```java
public class Balloon {

    private String color;

    public Balloon(){}

    public Balloon(String c){
        this.color=c;
    }

    public String getColor() {
        return color;
    }

    public void setColor(String color) {
        this.color = color;
    }
}
```
And we have a simple program with a generic method to swap two objects, the class looks like below.
```java
public class Test {

    public static void main(String[] args) {

        Balloon red = new Balloon("Red"); //memory reference 50
        Balloon blue = new Balloon("Blue"); //memory reference 100

        swap(red, blue);
        System.out.println("red color="+red.getColor());
        System.out.println("blue color="+blue.getColor());

        foo(blue);
        System.out.println("blue color="+blue.getColor());

    }

    private static void foo(Balloon balloon) { //baloon=100
        balloon.setColor("Red"); //baloon=100
        balloon = new Balloon("Green"); //baloon=200
        balloon.setColor("Blue"); //baloon = 200
    }

    //Generic swap method
    public static void swap(Object o1, Object o2){
        Object temp = o1;
        o1=o2;
        o2=temp;
    }
}
```
When we execute the above program, we get following output.
```text
red color=Red
blue color=Blue 
blue color=Red
```
If you look at the first two lines of the output, it’s clear that swap method didn’t work. This is because Java is passed by value, this swap() method test can be used with any programming language to check whether it’s pass by value or pass by reference.

Let’s analyze the program execution step by step.
```java
Balloon red = new Balloon("Red");
Balloon blue = new Balloon("Blue");
```
When we use the new operator to create an instance of a class, the instance is created and the variable contains the reference location of the memory where the object is saved. For our example, let’s assume that “red” is pointing to 50 and “blue” is pointing to 100 and these are the memory location of both Balloon objects.

Now when we are calling swap() method, two new variables o1 and o2 are created pointing to 50 and 100 respectively.

So below code snippet explains what happened in the swap() method execution.

```java
public static void swap(Object o1, Object o2){ //o1=50, o2=100
    Object temp = o1; //temp=50, o1=50, o2=100
    o1=o2; //temp=50, o1=100, o2=100
    o2=temp; //temp=50, o1=100, o2=50
} //method terminated
```
Notice that we are changing values of o1 and o2 but they are copies of “red” and “blue” reference locations, so actually, there is no change in the values of “red” and “blue” and hence the output.

If you have understood this far, you can easily understand the cause of confusion. Since the variables are just the reference to the objects, we get confused that we are passing the reference so Java is passed by reference. However, we are passing a copy of the reference and hence it’s pass by value. I hope it clears all the doubts now.

Now let’s analyze foo() method execution.
```java
private static void foo(Balloon balloon) { //baloon=100
    balloon.setColor("Red"); //baloon=100
    balloon = new Balloon("Green"); //baloon=200
    balloon.setColor("Blue"); //baloon = 200
}
```
The first line is the important one when we call a method the method is called on the Object at the reference location. At this point, the balloon is pointing to 100 and hence it’s color is changed to Red.

In the next line, balloon reference is changed to 200 and any further methods executed are happening on the object at memory location 200 and not having any effect on the object at memory location 100. This explains the third line of our program output printing blue color=Red.

I hope above explanation clear all the doubts, just remember that variables are references or pointers and its copy is passed to the methods, so Java is always passed by value. It would be more clear when you will learn about Heap and Stack memory and where different objects and references are stored.
