# Exercise 1: Control Statements and Loops

## Purpose

These exercises help you internalize control flow in Java. Understanding control statements isn't just about syntax—it's about **thinking algorithmically** and structuring logic.

---

## Exercise 1.1: Decision Making with if-else

### Task

Write a program that determines ticket price based on age:

- **Child** (0-12): $5
- **Teen** (13-17): $10
- **Adult** (18-64): $15
- **Senior** (65+): $12

**Requirements**:
1. Take age as input (or hardcode for now)
2. Use if-else to determine category
3. Print ticket price

### Extension

Add validation:
- What if age is negative?
- What if age is unreasonably high (e.g., 200)?

### Reflection

- How does if-else structure your thinking?
- Why test boundaries (12, 13, 17, 18, 64, 65)?
- How would you test this program?

---

## Exercise 1.2: Switch Statement

### Task

Write a program that displays day of week based on number:

- 1 → Monday
- 2 → Tuesday
- ... 7 → Sunday

**Requirements**:
1. Use switch statement
2. Handle invalid input (not 1-7)
3. Use default case

### Extension

Modify to accept day name (String) instead of number.

### Reflection

- When is switch better than if-else?
- Why is `break` important?
- What happens if you forget `break`?

---

## Exercise 1.3: Nested Conditions

### Task

Write a program for loan eligibility:

**Rules**:
- Must be 18+
- Must have income >= $30,000
- If income < $50,000: credit score must be >= 700
- If income >= $50,000: credit score must be >= 650

**Output**: Eligible or not, with reason if not eligible

### Reflection

- How do nested conditions model complex rules?
- How do you test all combinations?
- What makes this logic clear vs. confusing?

---

## Exercise 1.4: For Loop Basics

### Task

1. **Count from 1 to 10**:
   ```java
   for (int i = 1; i <= 10; i++) {
       System.out.println(i);
   }
   ```

2. **Count backwards from 10 to 1**

3. **Print even numbers from 2 to 20**

4. **Print multiplication table for 5** (5x1=5, 5x2=10, etc.)

### Reflection

- How does the for loop structure repetition?
- What's the relationship between initialization, condition, and increment?
- When would you use a for loop vs. while loop?

---

## Exercise 1.5: While Loop

### Task

1. **Sum numbers until user enters 0**:
   - Use while loop
   - Keep asking for input
   - Sum all inputs
   - Stop when 0 is entered

2. **Countdown timer**:
   - Start at 10
   - Decrement and print
   - Stop at 0

3. **Find factorial** (n! = n × (n-1) × ... × 1):
   - Use while loop
   - Example: 5! = 5 × 4 × 3 × 2 × 1 = 120

### Reflection

- When is while loop more appropriate than for loop?
- What's the danger of infinite loops?
- How do you ensure loop terminates?

---

## Exercise 1.6: Do-While Loop

### Task

Create a menu system:

```
1. Option 1
2. Option 2
3. Exit
Enter choice:
```

**Requirements**:
- Use do-while
- Display menu
- Get user choice
- Process choice
- Repeat until user chooses Exit

### Reflection

- Why use do-while here instead of while?
- What's guaranteed with do-while?
- When is this pattern useful?

---

## Exercise 1.7: For-Each Loop

### Task

1. **Create an array of names**:
   ```java
   String[] names = {"Alice", "Bob", "Charlie", "Diana"};
   ```

2. **Print all names using for-each**:
   ```java
   for (String name : names) {
       System.out.println(name);
   }
   ```

3. **Find longest name**:
   - Iterate through array
   - Track longest name
   - Print result

4. **Sum array of numbers**:
   ```java
   int[] numbers = {10, 20, 30, 40, 50};
   // Sum using for-each
   ```

### Reflection

- How is for-each simpler than traditional for loop?
- When can you use for-each?
- What can't you do with for-each? (e.g., modify array, need index)

---

## Exercise 1.8: Break and Continue

### Task

1. **Break Example**:
   - Loop from 1 to 100
   - Stop when you find a number divisible by 7 and 11
   - Use break to exit early

2. **Continue Example**:
   - Loop from 1 to 20
   - Print all numbers EXCEPT multiples of 3
   - Use continue to skip

3. **Practical Example**:
   - Search through array of names
   - Stop when you find "John" (use break)
   - Or: Print all names except "John" (use continue)

### Reflection

- When is break useful?
- When is continue useful?
- How do they alter normal loop flow?
- What's the difference between break and return?

---

## Exercise 1.9: Nested Loops

### Task

1. **Print pattern**:
   ```
   *
   **
   ***
   ****
   *****
   ```

2. **Multiplication table** (1-10):
   ```
   1x1=1  1x2=2  ... 1x10=10
   2x1=2  2x2=4  ... 2x10=20
   ...
   10x1=10 10x2=20 ... 10x10=100
   ```

3. **Find prime numbers** (1-50):
   - Use nested loops
   - Outer loop: numbers to check
   - Inner loop: check if divisible by any number

### Reflection

- How do nested loops work?
- What's the time complexity? (How many iterations?)
- When are nested loops necessary vs. inefficient?

---

## Exercise 1.10: Combining Control Structures

### Task

Create a simple calculator program:

**Menu**:
```
1. Add
2. Subtract
3. Multiply
4. Divide
5. Exit
```

**Requirements**:
- Use do-while for menu loop
- Use switch for operation choice
- Use if-else for validation (division by zero)
- Ask for two numbers
- Perform operation
- Display result
- Repeat until Exit

### Reflection

- How do different control structures work together?
- How does this structure make the program clear?
- How would you test this program?

---

## Exercise 1.11: Testing Your Code

### Task

For each program you wrote:

1. **Identify test cases**:
   - Normal cases
   - Boundary cases
   - Error cases

2. **Test manually**:
   - Run with different inputs
   - Verify output

3. **Think about automation**:
   - How would you automate testing?
   - What would test cases look like?

### Reflection

- How does writing code help you think like a tester?
- What defects might you find?
- How does control flow affect testability?

---

## 🎯 Self-Assessment

After completing these exercises, ask yourself:

1. Can I choose the right control structure for a problem?
2. Do I understand when to use if-else vs. switch?
3. Can I use loops effectively?
4. Do I understand break and continue?
5. Can I combine control structures?

---

## 💡 Key Insights to Carry Forward

- **Control flow structures logic** - Programs aren't just linear
- **Choose the right tool** - if-else for conditions, loops for repetition
- **Loops enable automation** - Repeat actions programmatically
- **Break/continue alter flow** - Exit or skip when needed
- **Nested structures model complexity** - Real problems need combinations

---

**Next Steps**: Once comfortable with control flow, move to Module 3: OOPs Concepts, where you'll organize code into classes and objects.

