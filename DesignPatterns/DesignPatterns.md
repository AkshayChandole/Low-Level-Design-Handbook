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

<br>

Using these patterns can lead to more organized, efficient, and modular code, which is easier to test and maintain.

<hr>


