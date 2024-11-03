# [Single Responsibility Principle (SRP)](#single-reponsibility-principle-srp)

<p align="center" >
 <img src="./images/srp.png" width="60%" >
</p>

The **Single Responsibility Principle (SRP)** is one of the five **SOLID principles** in object-oriented design, emphasizing that a class or module should have only one reason to change.

In other words, **a class should be responsible for only one part of a program's functionality**. This principle encourages a separation of concerns, making each class focused, easier to understand, and more maintainable.

### Key Benefits of SRP:
1. **Improved Readability**: Classes with a single responsibility are easier to read and understand since they handle only one functionality.
2. **Easier Maintenance**: Changes in one part of the application require modifications in only one class, reducing the risk of introducing bugs.
3. **Enhanced Testability**: With fewer functions, single-responsibility classes are simpler to test.
4. **Reduced Coupling**: The principle promotes low coupling by keeping concerns separated.

### Example of SRP in Java

Suppose we’re building a system for managing a book. 

Without SRP, a `Book` class might handle all aspects of book management, such as storing details, saving book data, and printing book information:

#### Without SRP:

```java
class Book {
    private String title;
    private String author;

    public Book(String title, String author) {
        this.title = title;
        this.author = author;
    }

    // Gets book details as a formatted string
    public String getBookDetails() {
        return title + " by " + author;
    }

    // Violates SRP: Handling persistence
    public void saveBook() {
        System.out.println("Saving book to database...");
    }

    // Violates SRP: Handling printing logic
    public void printBookDetails() {
        System.out.println(getBookDetails());
    }
}
```

Here, the `Book` class violates SRP because it’s responsible for:
- Storing book details
- Saving book data (persistence)
- Printing book information

This makes the class more complex, tightly coupled, and harder to maintain.

#### With SRP:

By applying SRP, we can split these responsibilities into separate classes:

```java
class Book {
    private String title;
    private String author;

    public Book(String title, String author) {
        this.title = title;
        this.author = author;
    }

    public String getBookDetails() {
        return title + " by " + author;
    }
}

// Handles persistence
class BookRepository {
    public void save(Book book) {
        System.out.println("Saving book to database...");
    }
}

// Handles printing
class BookPrinter {
    public void print(Book book) {
        System.out.println(book.getBookDetails());
    }
}
```

Here:
- The `Book` class is responsible only for storing book data.
- `BookRepository` handles saving the book data.
- `BookPrinter` manages printing book details.

Each class has a single responsibility, making the code easier to read, test, and maintain.
