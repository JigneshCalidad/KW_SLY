# Exercise 1: Java Basics Part 1

## Purpose

These exercises help you internalize Java fundamentals by writing code and understanding how it works.

---

## Exercise 1.1: Variables and Data Types

### Task

Create a Java program that:

1. Declares variables for:
   - Your name (String)
   - Your age (int)
   - Your height in meters (double)
   - Whether you like Java (boolean)

2. Initialize all variables with appropriate values

3. Print all variables with descriptive messages

### Example Output
```
My name is: John
My age is: 25
My height is: 1.75 meters
I like Java: true
```

### Reflection
- What's the difference between `int` and `double`?
- Why use `String` for name instead of `char`?

---

## Exercise 1.2: Operators

### Task

Create a program that demonstrates:

1. **Arithmetic operators**: Calculate and print:
   - Sum of two numbers
   - Difference
   - Product
   - Quotient
   - Remainder (modulus)

2. **Comparison operators**: Compare two numbers and print:
   - Is first greater than second?
   - Are they equal?
   - Is first less than or equal to second?

3. **Logical operators**: 
   - Check if a number is between 10 and 20
   - Check if a number is less than 5 OR greater than 15

### Reflection
- When would you use modulus (%) in real testing scenarios?
- How do logical operators help in test conditions?

---

## Exercise 1.3: Variable Naming and Conventions

### Task

1. Write code with **bad variable names**:
   ```java
   int a = 10;
   String x = "test";
   double d = 3.14;
   ```

2. Refactor to use **good variable names** following camelCase convention

3. Explain why good naming matters

### Reflection
- How does good naming help when reading code later?
- What makes a variable name "good"?

---

## Exercise 1.4: Type Conversion

### Task

1. Create variables of different types:
   - int: 100
   - double: 99.5
   - String: "50"

2. Perform conversions:
   - int to double (implicit)
   - double to int (explicit cast)
   - String to int (using Integer.parseInt())

3. Print results and observe what happens

### Reflection
- When does Java automatically convert types?
- What information is lost when converting double to int?
- Why is String to int conversion explicit?

---

## Exercise 1.5: Understanding JDK, JRE, JVM

### Task (Conceptual)

Answer these questions (you may need to research):

1. **What is the JVM?**
   - What does it do?
   - Why is it called "virtual"?

2. **What is the JRE?**
   - What does it contain?
   - Who uses it?

3. **What is the JDK?**
   - What does it contain beyond JRE?
   - Who uses it?

4. **Relationship**:
   - Draw a diagram showing how JDK, JRE, and JVM relate
   - Explain: "JDK includes JRE, JRE includes JVM"

### Reflection
- Why do you need JDK to write code, but users only need JRE?
- How does JVM enable "write once, run anywhere"?

---

## Exercise 1.6: Keywords

### Task

1. Try to use Java keywords as variable names:
   ```java
   int class = 10;  // This will cause an error
   String if = "test";  // This will cause an error
   ```

2. Observe the compiler errors

3. List 10 Java keywords and explain what each does

### Reflection
- Why are keywords reserved?
- How do keywords help structure Java programs?

---

## 🎯 Self-Assessment

After completing these exercises, ask yourself:

1. Can I explain the difference between primitive and reference types?
2. Do I understand when to use each data type?
3. Can I use operators correctly in expressions?
4. Do I follow Java naming conventions?
5. Do I understand the Java ecosystem (JDK, JRE, JVM)?

---

## 💡 Key Insights to Carry Forward

- **Types matter**: Java is strongly typed for safety
- **Naming matters**: Good names make code readable
- **Operators are tools**: Use the right operator for the task
- **Understanding the ecosystem**: JDK, JRE, JVM serve different purposes

---

**Next Steps**: Once comfortable with these basics, move to Module 2: Control Statements.

