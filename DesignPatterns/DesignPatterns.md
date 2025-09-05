# [Design Patterns](#design-patterns)

<p align="center" >
 <img src="./images/design-patterns.jpg" width="50%" >
</p>

Design Patterns are general, reusable solutions to common problems encountered in software design. 

They are templates or best practices that developers can follow when solving similar types of issues in various situations. 

Design patterns streamline the development process by providing a proven template for solving a problem in a particular context, which can help ensure code is more readable, maintainable, and scalable.

## [Classification of Design Patterns](#classification-of-design-patterns)

Design patterns are typically categorized into three main types:

### **[Creational Patterns:](#creational-patterns)** 
These deal with object creation mechanisms and aim to abstract or hide the instantiation process, making it easier to decouple code and provide greater flexibility in what gets created, how, and when.

Examples of creational patterns are -
 - [Singleton Pattern](CreationalPatterns/SingletonPattern.md)  
 - [Factory Method Pattern](CreationalPatterns/FactoryMethodPattern.md) 
 - [Abstract Factory Pattern](CreationalPatterns/AbstractFactoryPattern.md)
 - [Builder Pattern](CreationalPatterns/BuilderPattern.md) 
 - [Prototype Pattern](CreationalPatterns/PrototypePattern.md)

**When to use creational design patterns?**

| Creational Design Patterns | When to use |
| -------- | ------- |
| Factory pattern | <ul><li>When the type of objects required cannot be anticipated beforehand.</li><li>When multiple objects that share similar characteristics need to be created.</li><li>When you want to generalize the object instantiation process, since the object set up is complex in nature.</li></ul> |
| Constructor pattern | <ul><li>When you want to create multiple instances of the same template, since the instances can share methods but can still be different.</li><li>Useful in Libraries and Plugins design.</li></ul> |
| Singleton pattern | <ul><li>When a single object is needed to coordinate actions across a system.</li><li>When services store state, configuration, and provide access to resources.</li><li>Databases such as MongoDB utilize it for database connections.</li><li>When configuration objects don’t need multiple instances.</li></ul> |
| Builder pattern | <ul><li>When building complex objects whose construction process should be hidden.</li><li>Useful in apps requiring step-by-step object creation (e.g., DOM with nodes and attributes).</li></ul> |
| Prototype pattern | <ul><li>To eliminate the overhead of initializing an object.</li><li>When the system should be independent of how products are created.</li><li>When creating objects from a database and values are copied to the cloned object.</li></ul> |
| Abstract pattern | <ul><li>When applications require reuse or sharing of objects.</li><li>For applications with multiple families of related objects needing to be used together.</li><li>When object caching is required.</li><li>When the object creation process should be hidden from the client.</li></ul> |

 <br>

### **[Structural Patterns:](#structural-patterns)** 
These focus on class and object composition, defining relationships between entities to make them work together as a larger, flexible structure. They help organize classes and objects into more comprehensive and effective structures.

Examples of structural patterns are -
 - [Adapter Pattern](StructuralPatterns/AdapterPattern.md)
 - [Decorator Pattern](StructuralPatterns/DecoratorPattern.md)
 - [Proxy Pattern](StructuralPatterns/ProxyPattern.md)
 - [Composite Pattern](StructuralPatterns/CompositePattern.md)
 - [Facade Pattern](StructuralPatterns/FacadePattern.md)
 - [Flyweight Pattern](StructuralPatterns/FlyweightPattern.md)
 - [Bridge Pattern](StructuralPatterns/BridgePattern.md)

**When to use structural design patterns?**
| Structural Design Patterns | When to use |
| -------- | ------- |
| Decorator | <ul><li>To modify or extend the functionality of an object without changing its base code.</li><li>To implement additional functionalities of similar objects instead of reusing the same code.</li></ul> |
| Facade | <ul><li>To simplify a client’s interaction with a system by hiding the underlying complex code.</li><li>To interact with the methods present in a library without knowing the processing that happens in the background.</li></ul> |
| Adapter | <ul><li>To enable old APIs to work with new refactored ones.</li><li>To allow an object to cooperate with a class that has an incompatible interface.</li><li>To reuse the existing functionality of classes.</li></ul> |
| Bridge | <ul><li>To extend a class in several independent dimensions.</li><li>To change the implementation at run time.</li><li>To share the implementation between objects.</li></ul> |
| Composite | <ul><li>To allow the reuse of objects without worrying about their compatibility.</li><li>To develop a scalable application that uses plenty of objects.</li><li>To create a tree-like hierarchy of objects.</li></ul> |
| Flyweight | <ul><li>To share a list of immutable strings across the application.</li><li>To prevent load time as it allows caching.</li></ul> |
| Proxy | <ul><li>To reduce the workload on the target object.</li></ul> |

  
 <br>

### **[Behavioral Patterns:](#behavioral-patterns)** 
These deal with object interaction, communication, and responsibilities. Behavioral patterns help define the way objects collaborate and delegate responsibility, facilitating better management of complex flows and enabling greater flexibility.

Examples of behavioral patterns are -
 - [Strategy Pattern](BehavioralPatterns/StrategyPattern.md)
 - [Observer Pattern](BehavioralPatterns/ObserverPattern.md)
 - [Command Pattern](BehavioralPatterns/CommandPattern.md)
 - [Chain of Responsibility Pattern](BehavioralPatterns/ChainOfResponsibilityPattern.md)
 - [State Pattern](BehavioralPatterns/StatePattern.md)
 - [Iterator Pattern](BehavioralPatterns/IteratorPattern.md)
 - [Visitor Pattern](BehavioralPatterns/VisitorPattern.md)
 - [Template Method Pattern](BehavioralPatterns/TemplateMethodPattern.md)
 - [Mediator Pattern](BehavioralPatterns/MediatorPattern.md)
 - [Memento Pattern](BehavioralPatterns/MementoPattern.md)
 - [Interpreter Pattern](BehavioralPatterns/InterpreterPattern.md)

**When to use behavioral design patterns?**
| Behavioral Design Patterns | When to use |
| -------- | ------- |
| Chain of Responsibility | <ul><li>When a program needs to handle various requests differently without knowing the sequence and type of requests beforehand.</li><li>In event bubbling in the DOM, where the event propagates through nested elements and one of them may choose to handle it.</li></ul> |
| Command | <ul><li>To queue and execute requests at different times.</li><li>To perform “reset” or “undo” operations.</li><li>To keep a history of requests made.</li></ul> |
| Iterator | <ul><li>When dealing with problems explicitly related to iteration, for designing flexible looping constructs.</li><li>To access elements from a complex collection without knowing the underlying representation.</li><li>To implement a generic iterator that traverses any collection efficiently, independent of its type.</li></ul> |
| Mediator | <ul><li>To avoid tight coupling of objects in a system with many objects.</li><li>To improve code readability.</li><li>To make code easier to maintain.</li></ul> |
| Observer | <ul><li>To improve code management by breaking down large applications into loosely coupled objects.</li><li>To improve communication between different parts of the application.</li><li>To create a one-to-many dependency between loosely coupled objects.</li></ul> |
| Visitor | <ul><li>To perform operations across a group of related but different objects without changing their classes.</li><li>To add new operations to complex object structures without modifying the objects themselves.</li><li>To add extensibility to libraries or frameworks by allowing users to plug in new behaviors easily.</li></ul> |
| Interpreter | <ul><li>To build simple scripting languages or small domain-specific languages.</li><li>To define rules or grammar for processing expressions.</li><li>To interpret math expressions, search filters, or configuration scripts.</li></ul> |
| Memento | <ul><li>To implement undo and redo features in editors or applications.</li><li>To save snapshots of an object’s state without exposing its internal details.</li><li>To restore a system to a previous state when needed.</li></ul> |
| State | <ul><li>When an object’s behavior needs to change based on its internal state.</li><li>In scenarios like media players, game characters, or workflow steps.</li><li>To remove large if-else or switch statements related to state transitions.</li></ul> |
| Strategy | <ul><li>To select an algorithm at runtime based on the situation.</li><li>To swap out business rules or operations without changing the main logic.</li><li>For use cases like payment, sorting, or route-finding strategies.</li></ul> |
| Template Method | <ul><li>When multiple classes follow the same steps but need to change some of those steps.</li><li>To enforce a common structure for related processes.</li><li>In frameworks to let subclasses override parts of an algorithm.</li></ul> |


<br>

Using these patterns can lead to more organized, efficient, and modular code, which is easier to test and maintain.

<hr>


