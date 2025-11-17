# Module 4: Basics of Java Part 4 - Advanced Java

## 🌱 Why This Module Matters

This module covers **advanced Java features** that are essential for real-world programming and test automation. These aren't just syntax—they're **patterns and concepts** that make code more powerful, maintainable, and expressive.

Understanding these concepts enables you to:
- Write more sophisticated test code
- Understand Selenium's architecture
- Use test frameworks effectively
- Handle data and exceptions properly

---

## 📚 Learning Objectives

By the end of this module, you will understand:

1. **Methods & Constructors** - Organizing code
2. **POJOs** - Simple data containers
3. **Keywords** - static, this, super
4. **Access Modifiers** - Controlling visibility
5. **Collections** - Working with groups of data
6. **Exception Handling** - Managing errors
7. **String Handling** - Working with text
8. **Interfaces & Abstract Classes** - Defining contracts
9. **Data Structures** - Organizing data efficiently

---

## 🧩 Conceptual Overview

### Methods

**What they are**: Blocks of code that perform specific tasks.

**Syntax**:
```java
accessModifier returnType methodName(parameters) {
    // code
    return value;  // if not void
}
```

**Key concepts**:
- **Parameters**: Input to the method
- **Return type**: What the method gives back (void if nothing)
- **Method overloading**: Same name, different parameters

**Example**:
```java
public int add(int a, int b) {
    return a + b;
}
```

**Testing perspective**: Methods organize test logic into reusable, testable units.

---

### Constructor

**What it is**: Special method that **initializes objects** when created.

**Key points**:
- Same name as class
- No return type (not even void)
- Called automatically with `new`
- Can have parameters

**Example**:
```java
class User {
    String name;
    
    public User(String name) {  // Constructor
        this.name = name;
    }
}

User user = new User("John");  // Constructor called
```

**Purpose**: Ensure objects start in valid state.

---

### POJOs (Plain Old Java Objects)

**What they are**: Simple Java classes with:
- Private fields
- Public getters and setters
- No business logic (just data)

**Example**:
```java
public class User {
    private String name;
    private int age;
    
    public String getName() {
        return name;
    }
    
    public void setName(String name) {
        this.name = name;
    }
    // ... getters and setters for age
}
```

**Use case**: Representing test data, configuration, results.

---

### static Keyword

**What it means**: Belongs to the **class**, not instances.

**Key points**:
- Shared across all instances
- Accessed via class name (not object)
- Cannot access instance variables directly

**Example**:
```java
class Counter {
    static int count = 0;  // Shared by all instances
    
    static void increment() {
        count++;
    }
}

Counter.increment();  // Accessed via class name
```

**Use case**: Utility methods, constants, counters.

---

### this Keyword

**What it is**: Reference to the **current object**.

**Uses**:
- Distinguish instance variable from parameter
- Call other constructors
- Pass current object as parameter

**Example**:
```java
class User {
    String name;
    
    public User(String name) {
        this.name = name;  // this.name is instance variable
    }
}
```

---

### super Keyword

**What it is**: Reference to the **parent class**.

**Uses**:
- Call parent constructor
- Access parent methods
- Access parent variables

**Example**:
```java
class Parent {
    void display() {
        System.out.println("Parent");
    }
}

class Child extends Parent {
    void display() {
        super.display();  // Call parent's method
        System.out.println("Child");
    }
}
```

---

### Access Modifiers

**Control visibility**:
- **private**: Only within class
- **default**: Within package
- **protected**: Within package + subclasses
- **public**: Everywhere

**Principle**: Use most restrictive access that works (encapsulation).

---

### Collections

**What they are**: Framework for storing and manipulating groups of objects.

#### ArrayList

**Dynamic array** - Grows as needed.

**Example**:
```java
ArrayList<String> names = new ArrayList<>();
names.add("Alice");
names.add("Bob");
names.get(0);  // "Alice"
```

**Use case**: Lists of test data, dynamic collections.

#### HashMap

**Key-value pairs** - Fast lookup by key.

**Example**:
```java
HashMap<String, Integer> ages = new HashMap<>();
ages.put("Alice", 25);
ages.get("Alice");  // 25
```

**Use case**: Configuration data, test data lookup.

---

### Exception Handling

**What it is**: Managing errors gracefully.

**Keywords**:
- `try`: Code that might throw exception
- `catch`: Handle the exception
- `finally`: Always executes
- `throw`: Throw an exception
- `throws`: Declare exception in method signature

**Example**:
```java
try {
    int result = 10 / 0;
} catch (ArithmeticException e) {
    System.out.println("Cannot divide by zero");
} finally {
    System.out.println("Always executes");
}
```

**Types**:
- **Checked**: Must be handled (IOException)
- **Unchecked**: Runtime exceptions (NullPointerException)
- **Errors**: Serious problems (OutOfMemoryError)

**Testing perspective**: Handle exceptions in test code, don't let them crash tests.

---

### String Class

**Strings are objects** in Java.

**Key concepts**:
- **String pool**: Reuses string literals
- **Immutability**: Strings cannot be changed (new object created)
- **Methods**: length(), substring(), equals(), etc.

**Important**:
```java
String s1 = "Hello";
String s2 = "Hello";
s1 == s2;  // true (same object in pool)

String s3 = new String("Hello");
s1 == s3;  // false (different objects)
s1.equals(s3);  // true (same content)
```

**Use `.equals()` for comparison**, not `==`.

---

### Interfaces

**What they are**: Contracts that classes must implement.

**Syntax**:
```java
interface Drawable {
    void draw();  // Must be implemented
}

class Circle implements Drawable {
    public void draw() {
        // implementation
    }
}
```

**Key points**:
- Cannot be instantiated
- Methods are public and abstract (by default)
- Class can implement multiple interfaces

**Use case**: Define contracts, enable polymorphism.

---

### Abstract Classes

**What they are**: Classes that cannot be instantiated, must be extended.

**Can have**:
- Abstract methods (must be implemented)
- Concrete methods (can have implementation)
- Instance variables

**Example**:
```java
abstract class Animal {
    abstract void makeSound();  // Must implement
    
    void sleep() {  // Can use as-is
        System.out.println("Sleeping");
    }
}
```

**Difference from Interface**: Can have implementation, single inheritance.

---

### Data Structures

**Organizing data efficiently**:

#### LinkedList
- Elements linked via pointers
- Dynamic size
- Good for insertions/deletions

#### Circular LinkedList
- Last node points to first
- Circular structure

#### Doubly LinkedList
- Nodes have previous and next pointers
- Can traverse both directions

**Use case**: When you need specific access patterns.

---

### Garbage Collection

**What it is**: Automatic memory management.

**Concept**: Java automatically frees memory when objects are no longer referenced.

**You don't manage memory manually** (unlike C++).

---

### Equals and toString Overriding

**Object class** provides default implementations. Override for meaningful behavior.

**Example**:
```java
class User {
    String name;
    
    @Override
    public boolean equals(Object obj) {
        if (obj instanceof User) {
            return this.name.equals(((User) obj).name);
        }
        return false;
    }
    
    @Override
    public String toString() {
        return "User: " + name;
    }
}
```

---

### Wrapper Classes

**Primitive types have object wrappers**:
- int → Integer
- double → Double
- char → Character
- boolean → Boolean

**Use case**: When you need objects (Collections require objects).

---

### Comparator and Comparable

**For sorting objects**:

**Comparable**: Object defines how to compare itself
```java
class User implements Comparable<User> {
    public int compareTo(User other) {
        return this.name.compareTo(other.name);
    }
}
```

**Comparator**: External class defines comparison
```java
Comparator<User> byAge = (u1, u2) -> u1.age - u2.age;
```

---

## 🎯 Key Takeaways

1. **Methods organize code** - Reusable, testable units
2. **Constructors initialize** - Ensure valid state
3. **Collections manage data** - ArrayList, HashMap essential
4. **Exceptions must be handled** - Graceful error management
5. **Interfaces define contracts** - Enable polymorphism
6. **String handling is important** - Use equals(), understand immutability

---

## 📝 Exercises

See `exercises/` folder for hands-on practice.

---

## 🔗 Connections to Other Modules

- **Module 3**: Builds on OOPs concepts
- **Module 6**: Selenium uses all these concepts
- **Module 9**: Frameworks use collections, exceptions, interfaces

---

**Reflection Question**: How do these advanced Java features enable you to write more robust and maintainable test code?

