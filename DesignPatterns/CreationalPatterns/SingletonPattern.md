# [Singleton Pattern](#singleton-pattern)

## [What is Singleton Pattern?](#what-is-singleton-pattern)

The **Singleton Pattern** is a **creational design pattern** that ensures a class has **only one instance** throughout the application and provides a global point of access to that instance.

---

## [What Problem Does It Solve?](#what-problem-does-it-solve)

* Prevents multiple objects of the same class when only one is needed (e.g., configuration manager, logging, database connection pool).
* Provides **controlled global access** without using global variables.
* Saves resources by reusing a single instance.

---

## [Where Should It Be Used?](#where-should-it-be-used)

Use Singleton when:

* Exactly one object is needed to coordinate actions.
* You want a single shared resource (e.g., logger, cache, thread pool, configuration, database connection).
* You want to control concurrent access to shared resources.

Avoid Singleton when:

* You need multiple instances in the future.
* It may introduce hidden dependencies (global state is hard to test).

---

## [Real Life Example](#real-life-example)

* **Printer Spooler** → Only one spooler controls print jobs.
* **Logger** → A single log service writes messages from across the app.
* **Configuration Manager** → App-wide settings stored in one place.
* **Database Connection Pool** → A single instance manages access.

---

## [Class Diagram](#class-diagram)

Here’s a simple UML diagram for Singleton:

![Singleton Pattern UML](https://i.imgur.com/q5xC7Pb.png)

---

## [Implementations](#implementations)

<details>
<summary>Java</summary>

```java
public class Singleton {
    private static Singleton instance;

    private Singleton() { } // private constructor

    public static Singleton getInstance() {
        if (instance == null) {
            instance = new Singleton();
        }
        return instance;
    }
}

class Main {
    public static void main(String[] args) {
        Singleton obj1 = Singleton.getInstance();
        Singleton obj2 = Singleton.getInstance();
        System.out.println(obj1 == obj2); // true
    }
}
```

</details>

---

<details>
<summary>C++</summary>

```cpp
#include <iostream>
using namespace std;

class Singleton {
private:
    static Singleton* instance;
    Singleton() {} // private constructor
public:
    static Singleton* getInstance() {
        if (instance == nullptr) {
            instance = new Singleton();
        }
        return instance;
    }
};

Singleton* Singleton::instance = nullptr;

int main() {
    Singleton* obj1 = Singleton::getInstance();
    Singleton* obj2 = Singleton::getInstance();
    cout << (obj1 == obj2); // 1 (true)
}
```

</details>

---

<details>
<summary>Python</summary>

```python
class Singleton:
    _instance = None

    def __new__(cls):
        if cls._instance is None:
            cls._instance = super(Singleton, cls).__new__(cls)
        return cls._instance


obj1 = Singleton()
obj2 = Singleton()
print(obj1 is obj2)  # True
```

</details>

---

<details>
<summary>JavaScript</summary>

```javascript
class Singleton {
  constructor() {
    if (Singleton.instance) {
      return Singleton.instance;
    }
    Singleton.instance = this;
  }
}

const obj1 = new Singleton();
const obj2 = new Singleton();
console.log(obj1 === obj2); // true
```

</details>

---

## [Variations of Singleton](#variations-of-singleton)

1. **Eager Initialization** → Instance created at class loading time.

   * Pro: Thread safe automatically.
   * Con: Wastes memory if never used.

2. **Lazy Initialization** → Instance created when first needed.

   * Pro: Saves resources.
   * Con: Needs thread-safety measures.

3. **Thread-safe Singleton (Double-Checked Locking)**

   * Ensures only one instance in multithreaded environments.

4. **Bill Pugh Singleton (Java)** → Uses static inner class, best approach in Java.

---

Would you like me to also wrap the **thread-safe variations** (like double-checked locking, Bill Pugh, etc.) into collapsible sections for each language as well, so the wiki stays super neat?
