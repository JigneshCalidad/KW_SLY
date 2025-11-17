# Module 3: Basics of Java Part 3 - OOPs Concepts

## 🌱 Why This Module Matters

Object-Oriented Programming (OOPs) is a **way of thinking** about code. Instead of just writing instructions, you model **real-world concepts as objects** with properties and behaviors.

For testers, understanding OOPs is crucial because:
- Selenium uses OOPs extensively (WebDriver, WebElement are objects)
- Page Object Model (POM) is based on OOPs
- Test frameworks use OOPs concepts
- It helps you understand how code is organized

This module introduces the **fundamental concepts**—the building blocks of object-oriented thinking.

---

## 📚 Learning Objectives

By the end of this module, you will understand:

1. **Object** - Instances of classes
2. **Class** - Blueprints for objects
3. **Inheritance** - Reusing and extending code
4. **Polymorphism** - Same interface, different behavior
5. **Abstraction** - Hiding complexity
6. **Encapsulation** - Bundling data and methods

---

## 🧩 Conceptual Overview

### Object

**What it is**: An **instance** of a class. It has:
- **State** (attributes/properties): Data it holds
- **Behavior** (methods): Actions it can perform

**Real-world analogy**: A car is an object. It has properties (color, model) and behaviors (start, stop, accelerate).

**Example**:
```java
// Creating an object
String name = "John";  // name is an object of String class
```

**Concept**: Objects represent **things** in your program. They encapsulate related data and behavior.

---

### Class

**What it is**: A **blueprint** or template for creating objects.

**Analogy**: A class is like a cookie cutter. Objects are the cookies made from it.

**Syntax**:
```java
public class Car {
    // Attributes (state)
    String color;
    String model;
    
    // Methods (behavior)
    void start() {
        System.out.println("Car started");
    }
}
```

**Key points**:
- Class defines **what** objects of that type have (attributes)
- Class defines **what** objects of that type can do (methods)
- Objects are created from classes using `new`

**Example**:
```java
Car myCar = new Car();  // Creating an object from Car class
myCar.color = "Red";
myCar.start();
```

---

### Inheritance

**What it is**: A class can **inherit** attributes and methods from another class.

**Terminology**:
- **Parent class** (Superclass): The class being inherited from
- **Child class** (Subclass): The class that inherits

**Syntax**:
```java
class Parent {
    // parent attributes and methods
}

class Child extends Parent {
    // child can use parent's attributes and methods
    // child can add its own
}
```

**Concept**: "Is-a" relationship. A child **is a** type of parent.

**Example**:
```java
class Vehicle {
    void start() {
        System.out.println("Vehicle started");
    }
}

class Car extends Vehicle {
    // Car inherits start() method
    void honk() {
        System.out.println("Beep beep");
    }
}
```

**Benefits**:
- **Code reuse**: Don't repeat code
- **Extensibility**: Add new features easily
- **Maintainability**: Changes in parent affect children

**Testing perspective**: Base test classes can be inherited by specific test classes.

---

### Polymorphism

**What it is**: "Many forms." Same interface, different implementations.

**Types**:
1. **Compile-time** (Method overloading): Same method name, different parameters
2. **Runtime** (Method overriding): Child class provides its own implementation

**Method Overloading Example**:
```java
class Calculator {
    int add(int a, int b) {
        return a + b;
    }
    
    int add(int a, int b, int c) {  // Same name, different parameters
        return a + b + c;
    }
}
```

**Method Overriding Example**:
```java
class Animal {
    void makeSound() {
        System.out.println("Some sound");
    }
}

class Dog extends Animal {
    @Override
    void makeSound() {  // Override parent's method
        System.out.println("Woof");
    }
}
```

**Concept**: Polymorphism lets you write code that works with different types through a common interface.

**Testing perspective**: Different test classes can implement the same test interface differently.

---

### Abstraction

**What it is**: Hiding complexity, showing only essential features.

**Ways to achieve**:
1. **Abstract classes**: Cannot be instantiated, must be extended
2. **Interfaces**: Define contracts (what must be implemented)

**Abstract Class Example**:
```java
abstract class Shape {
    abstract void draw();  // Must be implemented by child
    
    void display() {  // Can have concrete methods
        System.out.println("Displaying shape");
    }
}

class Circle extends Shape {
    @Override
    void draw() {
        System.out.println("Drawing circle");
    }
}
```

**Concept**: Abstraction lets you define **what** must be done without specifying **how** (implementation details hidden).

**Testing perspective**: Abstract test base classes define structure, specific tests provide implementation.

---

### Encapsulation

**What it is**: Bundling data and methods together, controlling access.

**Access Modifiers**:
- **private**: Only accessible within the class
- **protected**: Accessible within package and subclasses
- **public**: Accessible everywhere
- **default** (no modifier): Accessible within package

**Example**:
```java
class BankAccount {
    private double balance;  // Private - cannot access directly
    
    public void deposit(double amount) {  // Public method to access
        if (amount > 0) {
            balance += amount;
        }
    }
    
    public double getBalance() {
        return balance;
    }
}
```

**Benefits**:
- **Data protection**: Prevent invalid states
- **Controlled access**: Methods validate before changing data
- **Maintainability**: Internal changes don't affect external code

**Concept**: Encapsulation is like a vending machine—you interact through buttons (public methods), not by reaching inside (private data).

**Testing perspective**: Test public interfaces, not internal implementation.

---

## 🎯 Key Takeaways

1. **Objects represent things** - With state and behavior
2. **Classes are blueprints** - Define what objects have and do
3. **Inheritance enables reuse** - Extend and customize
4. **Polymorphism provides flexibility** - Same interface, different behavior
5. **Abstraction hides complexity** - Show essential, hide details
6. **Encapsulation protects data** - Controlled access through methods

---

## 📝 Exercises

See `exercises/` folder for hands-on practice.

---

## 🔗 Connections to Other Modules

- **Module 4**: Builds on OOPs with advanced features
- **Module 6**: Selenium uses OOPs (WebDriver, WebElement)
- **Module 9**: Page Object Model is pure OOPs

---

**Reflection Question**: How does thinking in objects help you organize test code more effectively?

