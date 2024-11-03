# Low-Level-Design-Handbook

Low Level Design Interview Handbook

## [Object-Oriented Design (OOD)](📂%20ObjectOrientedDesign/📜%20README.md#object-oriented-design-ood)

- [Core Principles of OOD](📂%20ObjectOrientedDesign/📜%20README.md#core-principles-of-object-oriented-design-ood)
- [Encapsulation](📂%20ObjectOrientedDesign/📜%20README.md#encapsulation)
- [Abstraction](📂%20ObjectOrientedDesign/📜%20README.md#abstraction)
- [Inheritance](📂%20ObjectOrientedDesign/📜%20README.md#inheritance)
- [Polymorphism](📂%20ObjectOrientedDesign/📜%20README.md#polymorphism)
- [SOLID Principles](📂%20ObjectOrientedDesign/📂%20SolidPrinciples/SolidPrinciples.md#solid-principles)
  - [Single Responsibility Principle (SRP)](📂%20ObjectOrientedDesign/📂%20SolidPrinciples/SingleResponsibilityPrinciple.md#single-reponsibility-principle-srp)
  - [Open/Closed Principle (OCP)](📂%20ObjectOrientedDesign/📂%20SolidPrinciples/OpenClosedPrinciple.md#open-closed-principle-ocp)
  - [Liskov Substitution Principle (LSP)](📂%20ObjectOrientedDesign/📂%20SolidPrinciples/LiskovSubstitutionPrinciple.md#liskov-substitution-principle-lsp)
  - [Interface Segregation Principle (ISP)](📂%20ObjectOrientedDesign/📂%20SolidPrinciples/InterfaceSegregationPrinciple.md#interface-segregation-principle)
  - [Dependency Inversion Principle (DIP)](📂%20ObjectOrientedDesign/📂%20SolidPrinciples/DependencyInversionPrinciple.md#dependency-inversion-principle-dip)

<hr>

## [Design Patterns](DesignPatterns/DesignPatterns.md#design-patterns)
- Creational Patterns:
  - Singleton Pattern
  - Factory Method Pattern
  - Abstract Factory Pattern
  - Builder Pattern
  - Prototype Pattern
- Structural Patterns:
  - Adapter Pattern
  - Decorator Pattern
  - Proxy Pattern
  - Composite Pattern
  - Facade Pattern
  - Flyweight Pattern
  - Bridge Pattern
- Behavioral Patterns:
  - Strategy Pattern
  - Observer Pattern
  - Command Pattern
  - Chain of Responsibility Pattern
  - State Pattern
  - Iterator Pattern
  - Visitor Pattern
  - Template Method Pattern
  - Mediator Pattern
  - Memento Pattern
  - Interpreter Pattern

Designing Classes and Interfaces

- Best practices for class design
- Designing for change and scalability
- Interface vs Abstract Classes
- Immutability and Thread Safety
- Law of Demeter (Principle of Least Knowledge)

UML (Unified Modeling Language)

- Class Diagrams
- Object Diagrams
- Sequence Diagrams
- Activity Diagrams

Modular Design

- Separation of Concerns (SoC)
- High Cohesion and Low Coupling
- Package Design Principles
  - Reuse-Release Equivalence Principle (REP)
  - Common Closure Principle (CCP)
  - Common Reuse Principle (CRP)

Error Handling and Fault Tolerance (LLD Context)

- Handling Exceptions Gracefully
- Design Patterns for Error Handling (e.g., Null Object Pattern, Circuit Breaker at the LLD level)
- Logging Best Practices for LLD

Concurrency and Multi-threading in Low-Level Design

- Thread Management in Design
- Locks, Semaphores, and Monitors
- Thread-safe Collections (ConcurrentHashMap, CopyOnWriteArrayList)
- Design patterns for multi-threading (e.g., Producer-Consumer, Thread Pool)
- Optimistic vs Pessimistic Locking
- Deadlocks and Starvation

Event-Driven Design (within LLD scope)

- Event Loops and Handlers
- Observer Pattern for Event Handling
- Pub-Sub and Event Messaging at the Application Level

Caching (in LLD context)

- In-memory caching strategies
- Lazy Loading and Eager Loading in object designs
- Time-based or Size-based eviction policies

Testing in Low-Level Design

- Unit Testing and Test-Driven Development (TDD)
- Mocking and Dependency Injection in Testing
- Designing testable classes (loosely coupled, high cohesion)
- Integration Testing (within class/module scope)

Refactoring and Code Quality

- Clean Code Principles
- Refactoring Patterns (e.g., Extract Method, Move Method, Inline Method)
- Code Smells and Technical Debt
- Ensuring Maintainability
- Design for Reusability and Readability

Best Practices in Class and Method Design

- Cohesion and Coupling (low coupling, high cohesion)
- DRY (Don't Repeat Yourself)
- YAGNI (You Aren’t Gonna Need It)
- KISS (Keep It Simple, Stupid)
- Interface Segregation and Dependency Injection

Access Control and Security in LLD

- Principles of Least Privilege
- Designing for Secure Code (SQL Injection protection, input validation, etc.)
- Role-based Access Control (RBAC) in object models

Domain-Driven Design (DDD) at LLD Level

- Entities, Value Objects
- Repositories
- Aggregates (in object design context)
