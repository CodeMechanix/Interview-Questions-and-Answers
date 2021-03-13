### Question
What is Inversion of Control?

Inversion of Control (IoC) can be quite confusing when it is first encountered.

1. What is it?
2. Which problem does it solve?
3. When is it appropriate to use and when not?

---------------------

### Answer
The Inversion of Control (IoC) and Dependency Injection (DI) patterns are all about removing dependencies from your code.

For example, say your application has a text editor component and you want to provide spell checking. Your standard code would look something like this:

```java
public class TextEditor {

    private SpellChecker checker;

    public TextEditor() {
        this.checker = new SpellChecker();
    }
}
```
What we've done here creates a dependency between the TextEditor and the SpellChecker. In an IoC scenario we would instead do something like this:
```java
public class TextEditor {

    private IocSpellChecker checker;

    public TextEditor(IocSpellChecker checker) {
        this.checker = checker;
    }
}
```
In the first code example we are instantiating SpellChecker (this.checker = new SpellChecker();), which means the TextEditor class directly depends on the SpellChecker class.

In the second code example we are creating an abstraction by having the SpellChecker dependency class in TextEditor's constructor signature (not initializing dependency in class). This allows us to call the dependency then pass it to the TextEditor class like so:

```java
SpellChecker sc = new SpellChecker(); // dependency
TextEditor textEditor = new TextEditor(sc);
```
Now the client creating the TextEditor class has control over which SpellChecker implementation to use because we're injecting the dependency into the TextEditor signature.

--------------------

Inversion of Controls is about separating concerns.

Without IoC: You have a laptop computer and you accidentally break the screen. And darn, you find the same model laptop screen is nowhere in the market. So you're stuck.

With IoC: You have a desktop computer and you accidentally break the screen. You find you can just grab almost any desktop monitor from the market, and it works well with your desktop.

Your desktop successfully implements IoC in this case. It accepts a variety type of monitors, while the laptop does not, it needs a specific screen to get fixed.

----------------------

Suppose you are an object. And you go to a restaurant:

Without IoC: you ask for "apple", and you are always served apple when you ask more.

With IoC: You can ask for "fruit". You can get different fruits each time you get served. for example, apple, orange, or water melon.

So, obviously, IoC is preferred when you like the varieties.
