# Exercise 1: Testing Principles and Techniques

## Purpose

These exercises help you internalize the 7 key principles of testing and apply test design techniques. The goal isn't to memorize—it's to develop **testing intuition** that guides your decisions.

---

## Exercise 1.1: The 7 Principles in Practice

### Task

For each of the 7 principles, find a **real-world example** from your experience or create a scenario:

1. **Testing Shows Presence of Defects**
   - Example: A test you ran that found a bug
   - Reflection: Why couldn't that test prove there were no other bugs?

2. **Exhaustive Testing is Impossible**
   - Example: A feature with too many combinations to test all
   - Reflection: How did you decide what to test?

3. **Early Testing Saves Time and Money**
   - Example: A bug found late vs. early (or imagine one)
   - Reflection: What was the cost difference?

4. **Defects Cluster Together**
   - Example: An area where you found multiple bugs
   - Reflection: Why do you think defects clustered there?

5. **Pesticide Paradox**
   - Example: Tests that stopped finding bugs
   - Reflection: How would you update those tests?

6. **Testing is Context Dependent**
   - Example: Different testing approaches for different projects
   - Reflection: What made the approaches different?

7. **Absence-of-Errors Fallacy**
   - Example: Software that worked but wasn't useful
   - Reflection: What made it a failure despite working?

### Reflection

After completing this, ask yourself:
- Which principle resonates most with your experience?
- How do these principles guide your testing decisions?
- Can you think of a situation where multiple principles applied?

---

## Exercise 1.2: Risk-Based Testing

### Scenario

You're testing an e-commerce website with limited time. Features include:
- User registration/login
- Product search
- Shopping cart
- Payment processing
- Product reviews
- User profile
- Admin dashboard

### Task

1. **Identify Risks**:
   - List each feature
   - Rate probability (High/Medium/Low)
   - Rate impact (High/Medium/Low)
   - Calculate risk (Probability × Impact)

2. **Prioritize Testing**:
   - Which features get most testing time?
   - Which get least?
   - Justify your decisions

3. **Create Test Strategy**:
   - For high-risk features: What would you test?
   - For low-risk features: What's the minimum testing?

### Reflection

- How does risk assessment change your testing approach?
- What factors influence probability and impact?
- How would you explain your prioritization to stakeholders?

---

## Exercise 1.3: Equivalence Partitioning

### Scenario

A form accepts age (must be 18-65) and email address.

### Task

1. **Age Field**:
   - Identify equivalence partitions
   - Select test values from each partition
   - Explain why these partitions matter

2. **Email Field**:
   - Identify equivalence partitions
   - Select test values from each partition
   - Consider: valid format, invalid format, empty, too long

3. **Write Test Cases**:
   - Create test cases using your partitions
   - Explain coverage

### Example Structure

**Age Partitions**:
- Valid: 18-65 (e.g., 25, 40, 60)
- Invalid - too low: < 18 (e.g., 17, 0, -5)
- Invalid - too high: > 65 (e.g., 66, 100)
- Boundary: 18, 65 (boundary values)

### Reflection

- How does equivalence partitioning help you test efficiently?
- Why test boundaries separately?
- What partitions might you miss if you don't think systematically?

---

## Exercise 1.4: Boundary Value Analysis

### Scenario

A system calculates shipping cost:
- Free shipping: Orders $0-$50
- Standard shipping: Orders $50.01-$100 (cost: $5)
- Express shipping: Orders $100.01+ (cost: $10)

### Task

1. **Identify Boundaries**:
   - List all boundary values
   - Explain why each boundary matters

2. **Create Test Cases**:
   - Test values: just below, at, just above each boundary
   - Example: $49.99, $50.00, $50.01

3. **Expected Results**:
   - What should happen at each boundary?
   - What's the correct behavior?

### Reflection

- Why are boundaries often where defects occur?
- How does boundary testing complement equivalence partitioning?
- What happens if boundaries are off-by-one errors?

---

## Exercise 1.5: Decision Table Testing

### Scenario

A login system has these rules:
- If username is empty → Error: "Username required"
- If password is empty → Error: "Password required"
- If username doesn't exist → Error: "User not found"
- If password is wrong → Error: "Invalid password"
- If both correct → Success: "Login successful"

### Task

1. **Create Decision Table**:
   - Conditions: Username empty? Password empty? Username exists? Password correct?
   - Actions: Show error messages or success

2. **Fill Table**:
   - All combinations of conditions
   - Expected action for each

3. **Identify Test Cases**:
   - Each row = one test case
   - Write test scenarios

### Example Structure

| Username Empty | Password Empty | Username Exists | Password Correct | Action |
|----------------|----------------|-----------------|------------------|--------|
| Yes | Yes | - | - | "Username required" |
| No | Yes | - | - | "Password required" |
| No | No | No | - | "User not found" |
| No | No | Yes | No | "Invalid password" |
| No | No | Yes | Yes | "Login successful" |

### Reflection

- How does a decision table help you find missing test cases?
- What's the relationship between conditions and test cases?
- How would you handle more complex business rules?

---

## Exercise 1.6: State Transition Testing

### Scenario

A user account has states:
- **New**: Just registered, not verified
- **Verified**: Email verified, can login
- **Active**: Logged in
- **Suspended**: Violated terms
- **Deleted**: Account deleted

**Transitions**:
- New → Verified (verify email)
- Verified → Active (login)
- Active → Suspended (admin action)
- Active → Deleted (user deletes)
- Suspended → Active (admin reinstates)
- Any → Deleted (admin deletes)

### Task

1. **Draw State Diagram**:
   - States as circles
   - Transitions as arrows
   - Label each transition

2. **Identify Test Cases**:
   - Valid transitions (should work)
   - Invalid transitions (should be blocked)
   - Example: Can you go from New directly to Active? (No)

3. **Test Scenarios**:
   - Write test cases for valid paths
   - Write test cases for invalid attempts

### Reflection

- How does state thinking help you find defects?
- What invalid transitions might developers miss?
- How does this apply to testing workflows?

---

## Exercise 1.7: Functional vs Non-Functional Testing

### Scenario

You're testing a social media app.

### Task

1. **Functional Testing**:
   - List 5 functional test scenarios
   - Focus: Does it work? (What it does)

2. **Non-Functional Testing**:
   - List 5 non-functional test scenarios
   - Focus: How well does it work?
   - Include: Performance, Security, Usability, Compatibility

3. **Compare**:
   - How are the test approaches different?
   - Why do both matter?
   - Which is easier to automate? Why?

### Reflection

- Why might non-functional testing be overlooked?
- How do functional and non-functional defects differ in impact?
- What non-functional aspects matter most for this app?

---

## Exercise 1.8: Testing Levels

### Scenario

You're testing a banking application with these components:
- User authentication module
- Account balance module
- Transaction processing module
- Reporting module

### Task

1. **Unit Testing**:
   - What would you test at unit level?
   - Example: A method that calculates interest

2. **Integration Testing**:
   - What integrations would you test?
   - Example: Authentication + Account Balance

3. **System Testing**:
   - What end-to-end scenarios?
   - Example: User logs in, checks balance, makes transaction

4. **Acceptance Testing**:
   - What from user perspective?
   - Example: User can transfer money successfully

### Reflection

- How do testing levels complement each other?
- Why test at multiple levels?
- What defects are found at each level?

---

## 🎯 Self-Assessment

After completing these exercises, ask yourself:

1. Can I explain each of the 7 principles with examples?
2. Can I prioritize testing based on risk?
3. Can I use test design techniques systematically?
4. Do I understand when to use which technique?
5. Can I think about testing at different levels?

---

## 💡 Key Insights to Carry Forward

- **Principles guide practice** - They're not rules, they're wisdom
- **Risk-based thinking** - Focus where it matters most
- **Techniques are tools** - Choose the right tool for the situation
- **Systematic approach** - Techniques help you be thorough
- **Multiple perspectives** - Functional and non-functional both matter

---

**Next Steps**: Practice applying these techniques to real scenarios. The more you practice, the more intuitive they become.

