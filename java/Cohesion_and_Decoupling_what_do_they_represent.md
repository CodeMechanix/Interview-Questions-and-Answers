### Question
What are Cohesion and Decoupling? I found information about coupling but not about decoupling.


### Answer
Cohesion - related to the principle that a class/method should be responsible for one thing only i.e there are no stray methods that don't belong in the encapsulation; a method only does one thing. High/Low cohesion is the degree to which this holds.

Coupling - how interdependent different parts of the system are. e.g how and where there are dependencies. If two classes make calls to methods of each other then they are tightly coupled, as changing one would mean having to change the other. Decoupling is the process of making something that was tightly coupled less so, or not at all.

Flexible systems have High Cohesion and Loose Coupling.

------------------

'Coupling' is a term that describes the relationship between two entities in a software system (usually classes).

When a class uses another class, or communicates with it, it's said to 'depend' on that other class, and so these classes are 'coupled'. At least one of them 'knows' about the other.

The idea is that we should try to keep the coupling between classes in our systems as 'loose' as possible: hence 'loose coupling' or sometimes 'decoupling' (although in English 'decoupling' would mean 'no coupling at all', people often use it to imply 'loose coupling' between entities).

So: what is loose-coupling versus strong coupling in practice, and why should we make entities loosely-coupled?

Coupling describes the degree of dependency between one entity to another entity. Often classes or objects.

When ClassA depends heavily on ClassB, the chances of ClassA being affected when ClassB is changed are high. This is strong coupling.

However if ClassA depends lightly on ClassB, than the chances of ClassA being affected in any way by a change in the code of ClassB, are low. This is loose coupling, or a 'decoupled' relationship.

Loose coupling is good because we don't want the components of our system to heavily depend on each other. We want to keep our system modular, where we can safely change one part without affecting the other.

When two parts are loosely coupled, they are more independent of each other and are less likely to break when the other changes.

For example, when building a car, you wouldn't want an internal change in the engine to break something in the steering wheel.

While this would never happen by accident when building a car, similar things happen to programmers all the time. Loose coupling is meant to reduce the risk of such things happening.

Strong coupling usually occurs when entity A knows too much about entity B. If entity A makes too many assumptions about how entity B operates or how it is built, than there is a high risk that a change in entity B will affect entity A. This is because one of it's assumptions about entity B are now incorrect.

For example, imagine that as a driver, you would make certain assumptions about how the engine of your car works.

The day you buy a new car with an engine that works differently (or for some reason your engine was replaced), your previous assumptions would be incorrect. If you were code in a computer, you would now be incorrect code that doesn't work properly.

However, if all the assumptions that as a driver you made about cars is that: A- they have steering wheels and B- they have brake and gas pedals, than changes in the car won't affect you, as long as your few assumptions stay correct. This is loose coupling.

An important technique to achieve loose coupling is Encapsulation. The idea is that a class hides it's internal details from other classes, and offers a strictly defined interface for other classes to communicate with it.

So for example, if you were defining a class Car, it's interface (public methods) would probably be drive(), stop(), steerLeft(), steerRight(), getSpeed(). These are the methods other objects can invoke on Car objects.

All of the other details of the Car class: how the engine works, kind of fuel it uses, etc. are hidden from other classes - to prevent them from knowing too much about Car.

The moment class A knows too much about class B: we have a strongly coupled relationship, where class A is too dependent on class B and a change in class B is likely to affect class A. Making the system hard to expand and maintain.

A relationship between two entities, where they know little about each other (only what's necessary) - is a loosely coupled, or decoupled relationship.