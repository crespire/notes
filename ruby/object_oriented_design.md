# Object Oriented Design Notes

Approach to design is a little different from procedural programming. Talking through a problem's nouns typically yield **domain objects**. They are usually a good start to the design, but other important kind of object are abstraction objects, and the key to discovering them is to focus on the *messages* that are sent between your domain objects. "I need to send this message, who should respond to it?"

A focus on messages enables us to not only find out what objects we need that are not readily apparent in the domain objects, but also allows us to focus on the designing a sensible *public interface* for these objects. Public interfaces are the methods that your objects expose for other objects to work with.

Sequence diagrams using UML are helpful to draft up the classes and messages you will be sending. [https://sequencediagram.org/](https://sequencediagram.org/) is a site that helps you create diagrams.

Advantages to using sequence diagrams to help plan your objects and messages:

- See your program in terms of the messages that the objects pass back and fourth
- Visually shows you where your messages are going. Is this message going to the right receiver?