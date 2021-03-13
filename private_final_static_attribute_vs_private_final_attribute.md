### Question 
In Java, what's the difference between:
> private final static int NUMBER = 10;

and
> private final int NUMBER = 10;

Both are private and final, the difference is the static attribute.

### Answer
For final, it can be assigned different values at runtime when initialized. For example
```java
class Test{
  public final int a;
}

Test t1  = new Test();
t1.a = 10;
Test t2  = new Test();
t2.a = 20; //fixed
```
Thus each instance has different value of field a.

For static final, all instances share the same value, and can't be altered after first initialized.

```java
class TestStatic{
      public static final int a = 0;
}

TestStatic t1  = new TestStatic();
t1.a = 10; // ERROR, CAN'T BE ALTERED AFTER THE FIRST 
TestStatic t2  = new TestStatic();
t1.a = 20;   // ERROR, CAN'T BE ALTERED AFTER THE FIRST INITIALIZATION.
```