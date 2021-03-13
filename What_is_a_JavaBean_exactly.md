### Question
What is a JavaBean exactly?

I understood, I think, that a "Bean" is a Java class with properties and getters/setters. As much as I understand, it is the equivalent of a C struct. Is that true?

Also, is there a real syntactic difference between a bean and a regular class? Is there any special definition or an interface?

------------------------------------------------------

### Answer

JavaBeans are Java classes which adhere to an extremely simple coding convention. All you have to do is to

- The JavaBean class must implement either Serializable or Externalizable;
- The JavaBean class must have a public no-arg constructor;
- All JavaBean properties must have public setter and getter methods (as appropriate);
- All JavaBean instance variables should be private.
- Must have public class.