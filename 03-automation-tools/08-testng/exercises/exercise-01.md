# Exercise 1: TestNG Framework

## Purpose

These exercises help you understand TestNG not just as a tool, but as a **system for organizing and executing tests**. The goal is to develop intuition for when and how to use TestNG features effectively.

---

## Exercise 1.1: Basic TestNG Setup

### Task

1. **Add TestNG to Project**:
   - If using Maven, add dependency to `pom.xml`
   - If using Eclipse, install TestNG plugin
   - Verify installation

2. **Create First TestNG Test**:
   ```java
   import org.testng.annotations.Test;
   
   public class FirstTestNGTest {
       @Test
       public void firstTest() {
           System.out.println("This is my first TestNG test");
       }
   }
   ```

3. **Run the Test**:
   - Right-click → Run as TestNG Test
   - Observe test output
   - Check test results

### Reflection

- How is TestNG different from running Java main method?
- What does the @Test annotation do?
- How does TestNG organize test execution?

---

## Exercise 1.2: TestNG Annotations

### Task

Create a test class that demonstrates all annotations:

```java
import org.testng.annotations.*;

public class AnnotationDemo {
    @BeforeSuite
    public void beforeSuite() {
        System.out.println("Before Suite");
    }
    
    @BeforeTest
    public void beforeTest() {
        System.out.println("Before Test");
    }
    
    @BeforeClass
    public void beforeClass() {
        System.out.println("Before Class");
    }
    
    @BeforeMethod
    public void beforeMethod() {
        System.out.println("Before Method");
    }
    
    @Test
    public void test1() {
        System.out.println("Test 1");
    }
    
    @Test
    public void test2() {
        System.out.println("Test 2");
    }
    
    @AfterMethod
    public void afterMethod() {
        System.out.println("After Method");
    }
    
    @AfterClass
    public void afterClass() {
        System.out.println("After Class");
    }
    
    @AfterTest
    public void afterTest() {
        System.out.println("After Test");
    }
    
    @AfterSuite
    public void afterSuite() {
        System.out.println("After Suite");
    }
}
```

**Observe the execution order** and document it.

### Reflection

- What's the execution order?
- When would you use @BeforeMethod vs @BeforeClass?
- How do annotations help organize test setup and teardown?

---

## Exercise 1.3: Test Priority

### Task

Create tests with different priorities:

```java
@Test(priority = 3)
public void testC() {
    System.out.println("Test C - Priority 3");
}

@Test(priority = 1)
public void testA() {
    System.out.println("Test A - Priority 1");
}

@Test(priority = 2)
public void testB() {
    System.out.println("Test B - Priority 2");
}

@Test  // No priority specified
public void testD() {
    System.out.println("Test D - No priority");
}
```

**Run and observe execution order**.

### Reflection

- How does priority affect execution?
- What's the default priority?
- When is priority useful vs. dependencies?

---

## Exercise 1.4: Test Groups

### Task

1. **Create Tests with Groups**:
   ```java
   @Test(groups = "smoke")
   public void loginTest() {
       System.out.println("Smoke test: Login");
   }
   
   @Test(groups = "smoke")
   public void homePageTest() {
       System.out.println("Smoke test: Home page");
   }
   
   @Test(groups = "regression")
   public void searchTest() {
       System.out.println("Regression test: Search");
   }
   
   @Test(groups = {"smoke", "regression"})
   public void checkoutTest() {
       System.out.println("Smoke and Regression: Checkout");
   }
   ```

2. **Run Specific Groups**:
   - Create `testng.xml`:
     ```xml
     <suite name="TestSuite">
         <test name="SmokeTests">
             <groups>
                 <run>
                     <include name="smoke"/>
                 </run>
             </groups>
             <classes>
                 <class name="YourTestClass"/>
             </classes>
         </test>
     </suite>
     ```
   - Run only smoke tests
   - Run only regression tests

### Reflection

- How do groups help organize tests?
- When would you run only smoke tests?
- How do groups enable parallel execution strategies?

---

## Exercise 1.5: Test Dependencies

### Task

Create tests with dependencies:

```java
@Test
public void login() {
    System.out.println("Login");
    // Simulate login
}

@Test(dependsOnMethods = "login")
public void checkDashboard() {
    System.out.println("Check Dashboard");
    // This test depends on login
}

@Test(dependsOnMethods = {"login", "checkDashboard"})
public void logout() {
    System.out.println("Logout");
    // This depends on both previous tests
}

@Test(dependsOnMethods = "login", alwaysRun = true)
public void independentTest() {
    System.out.println("Independent test");
    // Runs even if login fails
}
```

**Run and observe**:
- What happens if login fails?
- What happens with `alwaysRun = true`?

### Reflection

- How do dependencies control test flow?
- When is `alwaysRun` useful?
- What are the pros and cons of dependencies?

---

## Exercise 1.6: DataProvider

### Task

Create parameterized tests using DataProvider:

```java
@DataProvider(name = "loginData")
public Object[][] getLoginData() {
    return new Object[][] {
        {"user1", "pass1", true},   // username, password, expected success
        {"user2", "pass2", true},
        {"invalid", "wrong", false},
        {"", "pass", false},  // empty username
        {"user", "", false}   // empty password
    };
}

@Test(dataProvider = "loginData")
public void loginTest(String username, String password, boolean expectedSuccess) {
    System.out.println("Testing login with: " + username);
    // Simulate login
    boolean actualSuccess = performLogin(username, password);
    // Assert
    Assert.assertEquals(actualSuccess, expectedSuccess, 
        "Login result mismatch for user: " + username);
}
```

### Reflection

- How does DataProvider enable data-driven testing?
- What's the relationship between DataProvider and test parameters?
- How does this reduce code duplication?

---

## Exercise 1.7: Parallel Execution

### Task

1. **Create Multiple Tests**:
   ```java
   @Test
   public void test1() {
       System.out.println("Test 1 - Thread: " + Thread.currentThread().getId());
       // Some test logic
   }
   
   @Test
   public void test2() {
       System.out.println("Test 2 - Thread: " + Thread.currentThread().getId());
   }
   
   @Test
   public void test3() {
       System.out.println("Test 3 - Thread: " + Thread.currentThread().getId());
   }
   ```

2. **Create testng.xml for Parallel Execution**:
   ```xml
   <suite name="ParallelSuite" parallel="methods" thread-count="3">
       <test name="ParallelTests">
           <classes>
               <class name="YourTestClass"/>
           </classes>
       </test>
   </suite>
   ```

3. **Run and Observe**:
   - Note thread IDs in output
   - Verify tests run in parallel

### Reflection

- How does parallel execution speed up tests?
- What challenges does parallel execution create?
- When is parallel execution beneficial?

---

## Exercise 1.8: Test Listeners

### Task

Create a custom listener:

```java
import org.testng.ITestListener;
import org.testng.ITestResult;

public class CustomListener implements ITestListener {
    @Override
    public void onTestStart(ITestResult result) {
        System.out.println("Test started: " + result.getName());
    }
    
    @Override
    public void onTestSuccess(ITestResult result) {
        System.out.println("Test passed: " + result.getName());
    }
    
    @Override
    public void onTestFailure(ITestResult result) {
        System.out.println("Test failed: " + result.getName());
        // Could take screenshot here
    }
    
    @Override
    public void onTestSkipped(ITestResult result) {
        System.out.println("Test skipped: " + result.getName());
    }
}
```

**Use the listener** in testng.xml:
```xml
<listeners>
    <listener class-name="CustomListener"/>
</listeners>
```

### Reflection

- How do listeners extend TestNG functionality?
- What can you do with listeners?
- When would you create custom listeners?

---

## Exercise 1.9: TestNG with Selenium

### Task

Create a complete Selenium test using TestNG:

```java
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
import org.testng.annotations.*;

public class SeleniumTestNGTest {
    WebDriver driver;
    
    @BeforeMethod
    public void setUp() {
        driver = new ChromeDriver();
        driver.get("https://www.example.com");
    }
    
    @Test
    public void testPageTitle() {
        String title = driver.getTitle();
        Assert.assertEquals(title, "Example Domain");
    }
    
    @Test
    public void testPageURL() {
        String url = driver.getCurrentUrl();
        Assert.assertTrue(url.contains("example.com"));
    }
    
    @AfterMethod
    public void tearDown() {
        driver.quit();
    }
}
```

### Reflection

- How does TestNG structure Selenium tests?
- Why use @BeforeMethod for setup?
- How does this pattern scale to multiple tests?

---

## Exercise 1.10: TestNG Reports

### Task

1. **Run Tests**:
   - Execute test suite
   - Let TestNG generate reports

2. **Explore Reports**:
   - Find `test-output` folder
   - Open `index.html` in browser
   - Explore different report sections

3. **Understand Report Information**:
   - Test summary
   - Pass/fail counts
   - Execution time
   - Failed test details

### Reflection

- How do reports help you understand test results?
- What information is most valuable?
- How would you use reports to communicate with stakeholders?

---

## 🎯 Self-Assessment

After completing these exercises, ask yourself:

1. Can I set up TestNG in a project?
2. Do I understand annotation execution order?
3. Can I use groups, priorities, and dependencies?
4. Can I create data-driven tests with DataProvider?
5. Can I configure parallel execution?
6. Can I integrate TestNG with Selenium?

---

## 💡 Key Insights to Carry Forward

- **TestNG organizes tests** - Annotations structure execution
- **Groups enable organization** - Run related tests together
- **Dependencies control flow** - Tests can depend on others
- **DataProvider enables data-driven testing** - One test, multiple scenarios
- **Parallel execution speeds up** - But requires proper setup
- **Listeners extend functionality** - Screenshots, logging, custom reports

---

**Next Steps**: Once comfortable with TestNG, move to Module 9: Frameworks to build Page Object Model and other automation frameworks.

