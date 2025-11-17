# Module 3: Software Development Advanced

## 🌱 Why This Module Matters

As a tester, you don't need to be a database expert or OOPs master, but understanding **SQL and OOPs concepts** helps you:
- Communicate effectively with developers
- Understand system architecture
- Write better test cases
- Debug issues more effectively
- Understand how data flows through systems

This module provides the **essential understanding** you need, not deep implementation details.

---

## 📚 Learning Objectives

By the end of this module, you will understand:

1. **SQL Fundamentals** - How to query databases for testing
2. **OOPs Concepts** - How object-oriented code is structured
3. **Testing Implications** - How these concepts affect testing

---

## 🧩 Conceptual Overview

### SQL (Structured Query Language)

**What it is**: Language for managing and querying **relational databases**.

**Why testers need it**:
- Verify data is stored correctly
- Set up test data
- Clean up after tests
- Verify database state
- Test data integrity

#### Core SQL Concepts

**Database Structure**:
- **Database**: Container for related data
- **Table**: Collection of rows and columns
- **Row (Record)**: Single data entry
- **Column (Field)**: Data attribute

**Key Operations**:

1. **SELECT**: Retrieve data
   ```sql
   SELECT * FROM users WHERE age > 18;
   ```

2. **INSERT**: Add data
   ```sql
   INSERT INTO users (name, email) VALUES ('John', 'john@example.com');
   ```

3. **UPDATE**: Modify data
   ```sql
   UPDATE users SET email = 'newemail@example.com' WHERE id = 1;
   ```

4. **DELETE**: Remove data
   ```sql
   DELETE FROM users WHERE id = 1;
   ```

**Testing perspective**: Use SQL to:
- Verify test data exists
- Check data after test execution
- Clean test environment
- Validate data integrity

---

### OOPs (Object-Oriented Programming)

**What it is**: Programming paradigm based on **objects** (data + behavior).

**Why testers need it**:
- Understand code structure
- Know what to test (methods, classes)
- Understand inheritance and polymorphism
- Communicate with developers

#### Core OOPs Concepts

**1. Object**
- Instance of a class
- Has attributes (data) and methods (behavior)
- Example: A specific user object with name, email, login()

**2. Class**
- Blueprint for objects
- Defines attributes and methods
- Example: User class defines what a user is

**3. Inheritance**
- Classes can inherit from other classes
- Child class gets parent's features
- Example: AdminUser inherits from User

**Testing perspective**: Test inherited methods, overridden methods, polymorphism

**4. Polymorphism**
- Same interface, different implementations
- Methods behave differently based on object type
- Example: calculateArea() works for Circle and Rectangle differently

**Testing perspective**: Test each implementation, test polymorphic behavior

**5. Abstraction**
- Hide complexity, show essential features
- Abstract classes define structure
- Example: Vehicle abstract class, Car and Bike implement it

**Testing perspective**: Test abstract class contracts, test implementations

**6. Encapsulation**
- Data and methods bundled together
- Access controlled (public, private, protected)
- Example: User class encapsulates user data and methods

**Testing perspective**: Test public interfaces, understand access levels

---

## 🎯 Key Takeaways

1. **SQL for data verification** - Essential for database testing
2. **OOPs for code understanding** - Helps you understand what to test
3. **Concepts, not mastery** - Understand enough to test effectively
4. **Communication tool** - Helps you talk to developers

---

## 📝 Exercises

See `exercises/` folder for hands-on practice.

---

## 🔗 Connections to Other Modules

- **Module 4**: Understanding code structure helps with white-box testing
- **Module 6**: Selenium uses OOPs concepts (Page Object Model)
- **Module 7**: API testing may involve database verification

---

**Reflection Question**: How does understanding SQL and OOPs make you a more effective tester?

