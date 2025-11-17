# Module 8: TestNG Framework

## 🌱 Why This Module Matters

TestNG isn't just a testing framework—it's a **test organization and execution system**. It provides structure for your tests, enabling you to:
- Organize tests logically
- Control execution order
- Run tests in parallel
- Generate reports
- Manage test data

Understanding TestNG transforms Selenium scripts from isolated code into a **cohesive test suite**.

---

## 📚 Learning Objectives

By the end of this module, you will understand:

1. **TestNG Introduction** - What it is and why it's used
2. **Annotations** - Organizing test execution
3. **Test Organization** - Suites, groups, priorities
4. **Parallel Execution** - Running tests simultaneously
5. **Dependencies** - Controlling test order
6. **Listeners** - Extending TestNG functionality
7. **Reports** - Understanding test results

---

## 🧩 Conceptual Overview

### TestNG Introduction

**What it is**: Testing framework for Java, inspired by JUnit but more powerful.

**Key features**:
- **Annotations**: Organize test methods
- **Test suites**: Group related tests
- **Parallel execution**: Run tests simultaneously
- **Dependencies**: Control execution order
- **Reports**: HTML and XML reports
- **Data providers**: Parameterize tests

**Why TestNG over JUnit**:
- More annotations
- Better parallel execution
- Flexible test configuration
- Better reporting

---

### Annotations

**What they are**: Metadata that tells TestNG how to execute methods.

**Core annotations**:

1. **@Test**: Marks a method as a test
   ```java
   @Test
   public void loginTest() {
       // test code
   }
   ```

2. **@BeforeMethod**: Runs before each test method
   ```java
   @BeforeMethod
   public void setUp() {
       driver = new ChromeDriver();
   }
   ```

3. **@AfterMethod**: Runs after each test method
   ```java
   @AfterMethod
   public void tearDown() {
       driver.quit();
   }
   ```

4. **@BeforeClass**: Runs once before all tests in class
5. **@AfterClass**: Runs once after all tests in class
6. **@BeforeSuite**: Runs before all tests in suite
7. **@AfterSuite**: Runs after all tests in suite

**Execution order**: Suite → Class → Method (before/after at each level)

---

### Test Organization

#### Test Suites

**XML configuration** defines test suites:
```xml
<suite name="TestSuite">
    <test name="LoginTests">
        <classes>
            <class name="LoginTest"/>
        </classes>
    </test>
</suite>
```

**Benefits**: Organize tests, control execution, share configuration.

#### Groups

**Group related tests**:
```java
@Test(groups = "smoke")
public void loginTest() { }

@Test(groups = "regression")
public void searchTest() { }
```

**Run specific groups**: `testng.xml` or command line.

#### Priority

**Control execution order**:
```java
@Test(priority = 1)
public void firstTest() { }

@Test(priority = 2)
public void secondTest() { }
```

**Lower numbers run first**.

---

### Parallel Execution

**What it is**: Running multiple tests simultaneously.

**Benefits**:
- **Faster execution**: Tests run concurrently
- **Better resource use**: Utilize multiple cores
- **Scalability**: Run on multiple machines (Grid)

**Configuration**:
```xml
<suite name="ParallelSuite" parallel="methods" thread-count="3">
```

**Parallel modes**:
- **methods**: Each test method in parallel
- **classes**: Each test class in parallel
- **tests**: Each `<test>` tag in parallel

**Session handling**: Each thread needs its own WebDriver instance.

---

### Dependencies

**Control test order**:
```java
@Test(dependsOnMethods = "loginTest")
public void dashboardTest() {
    // Only runs if loginTest passes
}
```

**Groups dependencies**:
```java
@Test(dependsOnGroups = "setup")
public void mainTest() { }
```

**Always run**: `alwaysRun = true` runs even if dependency fails.

---

### Listeners

**What they are**: Interfaces that listen to test execution events.

**Common listeners**:
- **ITestListener**: Test execution events
- **IReporter**: Report generation
- **IAnnotationTransformer**: Modify annotations

**Use cases**:
- Take screenshots on failure
- Log test execution
- Custom reporting
- Retry failed tests

**Example**:
```java
public class TestListener implements ITestListener {
    @Override
    public void onTestFailure(ITestResult result) {
        // Take screenshot
    }
}
```

---

### Failed Test Execution

**Rerun only failed tests**:
```java
@Test(retryAnalyzer = RetryAnalyzer.class)
public void flakyTest() { }
```

**Or use testng-failed.xml** (auto-generated after run).

---

### Reports

**Types**:
- **Console**: Output during execution
- **HTML**: Detailed HTML reports
- **XML**: For CI/CD integration
- **Emailable**: Summary email report

**Location**: `test-output/` folder by default.

**Customization**: Use listeners to customize reports.

---

## 🎯 Key Takeaways

1. **Annotations organize execution** - Before/after hooks, test methods
2. **Suites organize tests** - Logical grouping
3. **Parallel execution speeds up** - But requires proper setup
4. **Dependencies control order** - Tests can depend on others
5. **Listeners extend functionality** - Screenshots, logging, custom reports

---

## 📝 Exercises

See `exercises/` folder for hands-on practice.

---

## 🔗 Connections to Other Modules

- **Module 7**: TestNG organizes Selenium techniques
- **Module 9**: Frameworks use TestNG for execution
- **Module 10**: CI/CD runs TestNG tests

---

**Reflection Question**: How does TestNG's structure help you organize and maintain large test suites?

