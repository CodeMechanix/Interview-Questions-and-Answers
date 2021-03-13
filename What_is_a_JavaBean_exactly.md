### Question
What is a JavaBean exactly?

I understood, I think, that a "Bean" is a Java class with properties and getters/setters. As much as I understand, it is the equivalent of a C struct. Is that true?

Also, is there a real syntactic difference between a bean and a regular class? Is there any special definition or an interface?

------------------------------------------------------

### Answer

JavaBeans are Java classes which adhere to an extremely simple coding convention. All you have to do is to

- Implement the java.io.Serializable interface - to save the state of an object
- Use a public empty argument constructor - to instantiate the object
- Provide public getter/setter methods - to get and set the values of private variables (properties).