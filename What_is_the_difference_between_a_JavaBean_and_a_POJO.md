### Question
What is the difference between a JavaBean and a POJO?

I'm not sure about the difference. I'm using Hibernate and, in some books, they use JavaBean and POJO as an interchangeable term. I want to know if there is a difference, not just in the Hibernate context, but as general concepts.

------------------
### Answer

A JavaBean follows certain conventions. Getter/setter naming, having a public default constructor, being serialisable etc.

A POJO (plain-old-Java-object) isn't rigorously defined. It's a Java object that doesn't have a requirement to implement a particular interface or derive from a particular base class, or make use of particular annotations in order to be compatible with a given framework, and can be any arbitrary (often relatively simple) Java object.

```java
/*
Java beans:                                Pojo:
-must extends serializable                  -no need to extends or implement.
 or externalizable.                     
-must have public class .                   - must have public class
-must have private instance variables.          -can have any access specifier variables.
-must have public setter and getter method.     - may or may not have setter or getter method.
-must have no-arg constructor.              - can have constructor with agruments.
*/
```