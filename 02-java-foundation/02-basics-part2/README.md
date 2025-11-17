# Module 2: Basics of Java Part 2

## 🌱 Why This Module Matters

Control statements are how you **make decisions** and **repeat actions** in code. They're the logic that makes programs dynamic—responding to conditions and performing repetitive tasks.

Understanding control flow is essential for test automation, where you need to:
- Make decisions (if element exists, click it)
- Repeat actions (test multiple users, iterate through test data)
- Handle different scenarios (positive/negative testing)

---

## 📚 Learning Objectives

By the end of this module, you will understand:

1. **Control Statements** - Directing program flow
2. **Decision Making** - if-else, switch
3. **Loops** - Repeating actions
4. **Jump Statements** - break, continue

---

## 🧩 Conceptual Overview

### Control Statements

**What they are**: Statements that control the **flow of execution** in a program.

**Types**:
- **Decision making**: Choose between paths (if-else, switch)
- **Looping**: Repeat actions (for, while, do-while)
- **Jumping**: Alter flow (break, continue)

**Concept**: Programs aren't just linear—they branch, loop, and jump based on conditions.

---

### Decision Making Statements

#### if-else

**Purpose**: Execute code based on a condition.

**Syntax**:
```java
if (condition) {
    // code if condition is true
} else {
    // code if condition is false
}
```

**Concept**: Like a fork in the road—if condition is true, go one way; otherwise, go another.

**Example**:
```java
int age = 20;
if (age >= 18) {
    System.out.println("Adult");
} else {
    System.out.println("Minor");
}
```

**Variations**:
- `if` alone (no else)
- `if-else if-else` (multiple conditions)
- Nested if (if inside if)

**Testing perspective**: Use for conditional test execution (if element exists, test it).

---

#### switch

**Purpose**: Choose from multiple options based on a value.

**Syntax**:
```java
switch (variable) {
    case value1:
        // code
        break;
    case value2:
        // code
        break;
    default:
        // code if no match
}
```

**Concept**: Like a menu—based on the value, execute corresponding code.

**Key points**:
- `break` exits the switch (without it, execution falls through)
- `default` handles unmatched cases
- Works with: int, char, String, enum

**Example**:
```java
String day = "Monday";
switch (day) {
    case "Monday":
        System.out.println("Start of week");
        break;
    case "Friday":
        System.out.println("End of week");
        break;
    default:
        System.out.println("Midweek");
}
```

**When to use**: Multiple discrete values (better than many if-else).

---

### Loop Statements

**Purpose**: Repeat code multiple times.

**Concept**: Instead of writing the same code many times, loops let you write it once and repeat it.

---

#### for loop

**Purpose**: Repeat a specific number of times.

**Syntax**:
```java
for (initialization; condition; increment) {
    // code to repeat
}
```

**Flow**:
1. Initialize (once)
2. Check condition
3. If true: execute code, then increment
4. Repeat from step 2

**Example**:
```java
for (int i = 0; i < 5; i++) {
    System.out.println("Count: " + i);
}
// Prints: Count: 0, Count: 1, Count: 2, Count: 3, Count: 4
```

**Use case**: When you know how many times to repeat.

**Testing perspective**: Test multiple users, iterate through test data.

---

#### while loop

**Purpose**: Repeat while condition is true.

**Syntax**:
```java
while (condition) {
    // code to repeat
}
```

**Flow**:
1. Check condition
2. If true: execute code
3. Repeat from step 1

**Key point**: Condition checked **before** each iteration.

**Example**:
```java
int count = 0;
while (count < 5) {
    System.out.println("Count: " + count);
    count++;
}
```

**Use case**: When you don't know how many times, but know the condition.

**Testing perspective**: Wait for element to appear, retry failed operations.

---

#### do-while loop

**Purpose**: Repeat while condition is true, but **execute at least once**.

**Syntax**:
```java
do {
    // code to repeat
} while (condition);
```

**Key difference**: Condition checked **after** each iteration (guarantees at least one execution).

**Example**:
```java
int count = 0;
do {
    System.out.println("Count: " + count);
    count++;
} while (count < 5);
```

**Use case**: When you need to execute at least once, then check condition.

---

#### for-each loop (Enhanced for loop)

**Purpose**: Iterate through collections (arrays, lists).

**Syntax**:
```java
for (dataType item : collection) {
    // code using item
}
```

**Concept**: "For each item in the collection, do something."

**Example**:
```java
String[] names = {"Alice", "Bob", "Charlie"};
for (String name : names) {
    System.out.println(name);
}
```

**Advantage**: Simpler than traditional for loop when iterating collections.

**Testing perspective**: Test all items in a list, verify all elements on a page.

---

### Jump Statements

**Purpose**: Alter normal flow of loops or switches.

---

#### break statement

**Purpose**: Exit loop or switch immediately.

**Example**:
```java
for (int i = 0; i < 10; i++) {
    if (i == 5) {
        break; // Exit loop when i is 5
    }
    System.out.println(i);
}
// Prints: 0, 1, 2, 3, 4
```

**Use case**: Exit early when condition met (found what you're looking for).

---

#### continue statement

**Purpose**: Skip to next iteration of loop.

**Example**:
```java
for (int i = 0; i < 10; i++) {
    if (i % 2 == 0) {
        continue; // Skip even numbers
    }
    System.out.println(i);
}
// Prints: 1, 3, 5, 7, 9
```

**Use case**: Skip certain iterations (skip invalid test data).

---

## 🎯 Key Takeaways

1. **Control flow directs execution** - Programs branch and loop
2. **if-else for decisions** - Choose based on conditions
3. **Loops for repetition** - Different loops for different needs
4. **break/continue alter flow** - Exit or skip iterations
5. **Choose the right construct** - Match the tool to the task

---

## 📝 Exercises

See `exercises/` folder for hands-on practice.

---

## 🔗 Connections to Other Modules

- **Module 1**: Uses variables and operators
- **Module 3**: OOPs uses control statements
- **Module 6**: Selenium uses loops and conditions extensively

---

**Reflection Question**: How do control statements enable you to write dynamic, responsive test code?

