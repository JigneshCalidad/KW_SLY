# Module 2: Software Development Fundamentals

## 🌱 Why This Module Matters

To test effectively, you must understand **how software is built**. This module explores the software development lifecycle and models—not just to memorize them, but to understand **when and where testing fits** into the development process.

Understanding development models helps you:
- Know **when** to test (at which stage)
- Understand **what** to test (what's ready at each stage)
- Communicate effectively with developers
- Plan testing activities strategically

---

## 📚 Learning Objectives

By the end of this module, you will understand:

1. **Software Development Life Cycle (SDLC)** - The phases software goes through
2. **Development Models** - Different approaches to building software
3. **Use Cases** - How requirements are expressed
4. **Software Requirement Specifications (SRS)** - The foundation of testing

---

## 🧩 Conceptual Overview

### Software Development Life Cycle (SDLC)

SDLC describes the **phases** software goes through from conception to retirement:

1. **Requirements Gathering** - Understanding what needs to be built
2. **Analysis** - Breaking down requirements into specifications
3. **Design** - Planning how to build it
4. **Implementation** - Writing the code
5. **Testing** - Verifying it works
6. **Deployment** - Releasing to users
7. **Maintenance** - Ongoing support and updates

**Testing insight**: Testing isn't just one phase—it's integrated throughout. Each phase has testing activities.

---

### Software Development Models

Different models organize these phases differently. Each has implications for testing:

#### 1. Waterfall Model

**Concept**: Sequential phases, each must complete before the next begins.

```
Requirements → Design → Implementation → Testing → Deployment
```

**Testing perspective**:
- ✅ Clear phases, easy to plan testing
- ❌ Testing happens late (defects found late)
- ❌ Changes are expensive
- **When to test**: Primarily in the Testing phase, but reviews possible earlier

**Use case**: Well-understood requirements, stable projects

---

#### 2. V-V Model (Verification & Validation)

**Concept**: Each development phase has a corresponding testing phase.

```
Requirements → System Testing
    Design → Integration Testing
Implementation → Unit Testing
```

**Testing perspective**:
- ✅ Testing planned from the start
- ✅ Each phase verified before moving on
- ❌ Still sequential, changes expensive
- **When to test**: Parallel to development, at each level

**Use case**: Safety-critical systems, regulated industries

---

#### 3. Iterative and Incremental Model

**Concept**: Build in cycles, adding functionality incrementally.

```
Iteration 1: Basic features → Test → Feedback
Iteration 2: More features → Test → Feedback
Iteration 3: Refinements → Test → Feedback
```

**Testing perspective**:
- ✅ Early testing of core features
- ✅ Continuous feedback
- ✅ Can adapt to changes
- **When to test**: At the end of each iteration

**Use case**: When requirements evolve, large projects

---

#### 4. Spiral Model

**Concept**: Risk-driven, combines iterative development with systematic aspects.

Each spiral includes:
- Planning
- Risk analysis
- Engineering (development)
- Evaluation (testing)

**Testing perspective**:
- ✅ Risk-focused approach
- ✅ Early risk identification
- ✅ Prototyping and testing early
- **When to test**: Throughout each spiral, with emphasis on risk areas

**Use case**: High-risk projects, complex systems

---

#### 5. Agile Model

**Concept**: Iterative, collaborative, adaptive. Values:
- Individuals and interactions over processes
- Working software over documentation
- Customer collaboration over contract negotiation
- Responding to change over following a plan

**Common frameworks**: Scrum, Kanban, XP

**Testing perspective**:
- ✅ Testing integrated throughout
- ✅ Continuous feedback
- ✅ Testers part of the team
- ✅ Test-driven development (TDD) possible
- **When to test**: Continuously, in every sprint/iteration

**Use case**: Rapidly changing requirements, customer-focused projects

---

#### 6. RAD Model (Rapid Application Development)

**Concept**: Rapid prototyping, quick iterations, user feedback.

**Testing perspective**:
- ✅ Early user feedback
- ✅ Quick validation
- ❌ May sacrifice quality for speed
- **When to test**: Continuously, with each prototype

**Use case**: Time-sensitive projects, proof of concepts

---

### Use Cases

**What they are**: Descriptions of **how users interact with the system** to achieve goals.

**Structure**:
- **Actor**: Who uses the system
- **Goal**: What they want to accomplish
- **Steps**: How they accomplish it
- **Preconditions**: What must be true before
- **Postconditions**: What's true after

**Example**:
```
Use Case: User logs in
Actor: Registered user
Goal: Access their account
Preconditions: User has account, on login page
Steps:
  1. Enter username
  2. Enter password
  3. Click "Login"
Postconditions: User is logged in, sees dashboard
```

**Testing insight**: Use cases are **test scenarios**. Each use case becomes test cases.

---

### Software Requirement Specifications (SRS)

**What they are**: Detailed document describing **what** the software should do (not how).

**Components**:
- Functional requirements (what it does)
- Non-functional requirements (how well it does it)
- Constraints (limitations)
- Assumptions (what we assume)

**Testing perspective**: SRS is the **foundation of testing**:
- Test cases derived from requirements
- Requirements traceability ensures coverage
- Missing/ambiguous requirements = testing challenges

**Key principle**: If it's not in the SRS, it's not a requirement. If it's in the SRS, it must be testable.

---

## 🎯 Key Takeaways

1. **Testing fits into every model** - But timing and approach differ
2. **Agile emphasizes continuous testing** - Testing is integrated, not separate
3. **Use cases are test scenarios** - They describe user interactions to test
4. **SRS is the testing foundation** - Requirements drive test cases
5. **Model choice affects testing strategy** - Adapt your approach to the model

---

## 📝 Exercises

See `exercises/` folder for hands-on practice.

---

## 🔗 Connections to Other Modules

- **Module 1**: Development models determine when testing starts
- **Module 4**: Testing levels map to development phases
- **Module 8**: Tools support different development models

---

**Reflection Question**: How does understanding development models help you plan testing activities more effectively?

