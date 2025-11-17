# Module 1: Basics of Java Part 1

## 🌱 Why This Module Matters

Java is the foundation for Selenium automation. Understanding Java isn't just about syntax—it's about understanding **how code structures thought** and how objects represent concepts.

This module establishes the **fundamental building blocks**: variables, data types, operators. These aren't just technical details—they're the **vocabulary** you need to express testing logic in code.

---

## 📚 Learning Objectives

By the end of this module, you will understand:

1. **Java Introduction** - What Java is and why it matters
2. **JDK, JRE, JVM** - The Java ecosystem
3. **Variables** - Storing and manipulating data
4. **Data Types** - Different kinds of data
5. **Operators** - Performing operations
6. **Keywords** - Reserved words with special meaning

---

## 🧩 Conceptual Overview

### Introduction to Java

**What Java is**: A programming language designed for:
- **Platform independence** - Write once, run anywhere (JVM)
- **Object-oriented** - Code organized as objects
- **Strongly typed** - Types are enforced
- **Widely used** - Enterprise applications, Android, automation

**Why testers learn Java**:
- Selenium uses Java
- Many test frameworks use Java
- Understanding code helps you test better
- Enables test automation

**Philosophy**: Java emphasizes **clarity and structure**—code should be readable and maintainable.

---

### JDK, JRE, and JVM

Understanding the Java ecosystem:

**JVM (Java Virtual Machine)**:
- **What**: Runs Java bytecode
- **Role**: Executes Java programs
- **Analogy**: Like an interpreter that understands Java bytecode

**JRE (Java Runtime Environment)**:
- **What**: JVM + libraries needed to run Java programs
- **Contains**: JVM + standard libraries
- **Use case**: Running Java applications (end users)

**JDK (Java Development Kit)**:
- **What**: JRE + tools to develop Java programs
- **Contains**: JRE + compiler (javac) + other tools
- **Use case**: Developing Java applications (developers/testers)

**Relationship**: JDK includes JRE, JRE includes JVM

**For testing**: You need JDK to write and run test code.

---

### Variables

**What they are**: Named storage locations that hold data.

**Concept**: Variables are like **labeled boxes** that hold values. The label (name) lets you refer to the value.

**Syntax**:
```java
dataType variableName = value;
```

**Example**:
```java
int age = 25;
String name = "John";
```

**Key concepts**:
- **Declaration**: Creating the variable
- **Initialization**: Giving it a value
- **Assignment**: Changing the value

**Naming rules**:
- Start with letter or underscore
- Can contain letters, digits, underscore
- Case-sensitive
- Cannot be keywords

**Naming conventions** (best practices):
- camelCase for variables (userName, totalCount)
- Meaningful names (age, not a)

---

### Data Types

**What they are**: Categories that define what kind of data a variable can hold.

**Why they matter**: Java is **strongly typed**—you must declare the type, and it's enforced.

#### Primitive Data Types

**Built-in types**:

1. **byte**: 8-bit integer (-128 to 127)
2. **short**: 16-bit integer
3. **int**: 32-bit integer (most common)
4. **long**: 64-bit integer
5. **float**: 32-bit floating point
6. **double**: 64-bit floating point (most common for decimals)
7. **char**: Single character ('a', '1')
8. **boolean**: true or false

**Memory perspective**: Different types use different amounts of memory. Choose the right type for efficiency.

#### Reference Data Types

**Objects** (we'll cover in detail later):
- **String**: Text ("Hello")
- **Arrays**: Collections of data
- **Classes**: Custom types

**Key difference**: Primitives store values directly. References store addresses to objects.

---

### Operators

**What they are**: Symbols that perform operations on operands.

#### Arithmetic Operators
- `+` Addition
- `-` Subtraction
- `*` Multiplication
- `/` Division
- `%` Modulus (remainder)

**Example**:
```java
int sum = 5 + 3;        // 8
int remainder = 10 % 3; // 1
```

#### Comparison Operators
- `==` Equal to
- `!=` Not equal to
- `>` Greater than
- `<` Less than
- `>=` Greater than or equal
- `<=` Less than or equal

**Return**: boolean (true/false)

**Example**:
```java
boolean isGreater = 5 > 3; // true
```

#### Logical Operators
- `&&` AND (both must be true)
- `||` OR (at least one true)
- `!` NOT (negation)

**Example**:
```java
boolean result = (age > 18) && (hasLicense); // both must be true
```

#### Assignment Operators
- `=` Assignment
- `+=` Add and assign
- `-=` Subtract and assign
- `*=` Multiply and assign
- `/=` Divide and assign

**Example**:
```java
int count = 5;
count += 3; // count is now 8 (same as count = count + 3)
```

---

### Keywords

**What they are**: Reserved words with special meaning in Java.

**Cannot be used as**: Variable names, class names, etc.

**Common keywords**:
- `class`, `public`, `private`, `protected`
- `if`, `else`, `for`, `while`, `do`
- `int`, `String`, `boolean`, `void`
- `return`, `new`, `this`, `super`
- `static`, `final`, `abstract`

**Purpose**: Keywords define the **structure** of Java programs.

---

## 🎯 Key Takeaways

1. **Java is strongly typed** - Types matter, they're enforced
2. **Variables store data** - Named storage with types
3. **Operators perform operations** - Arithmetic, comparison, logical
4. **JDK for development** - You need JDK to write code
5. **Keywords are reserved** - Cannot use as names

---

## 📝 Exercises

See `exercises/` folder for hands-on practice.

---

## 🔗 Connections to Other Modules

- **Module 2**: Control statements use operators and variables
- **Module 3**: OOPs builds on these fundamentals
- **Module 6**: Selenium uses Java concepts

---

**Reflection Question**: How does understanding data types help you write better test code?

