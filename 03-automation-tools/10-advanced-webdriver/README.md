# Module 10: Advanced WebDriver Techniques

## 🌱 Why This Module Matters

This module covers **advanced techniques** that handle real-world complexities: waits, screenshots, headless browsers, JavaScript execution, and more. These aren't just "nice to have" features—they're **essential for robust automation**.

Understanding these techniques enables you to:
- Handle timing issues (waits)
- Debug failures (screenshots)
- Run tests efficiently (headless)
- Interact with complex UI (JavaScript)
- Integrate with CI/CD (Maven, Jenkins)

---

## 📚 Learning Objectives

By the end of this module, you will understand:

1. **Waits** - Handling timing issues
2. **Screenshots** - Capturing test state
3. **Headless Browsers** - Running without UI
4. **JavaScript Execution** - Advanced interactions
5. **iFrame Handling** - Nested content
6. **Maven Integration** - Build management
7. **Jenkins Integration** - CI/CD
8. **Exception Handling** - Robust error management

---

## 🧩 Conceptual Overview

### Waits in Selenium

**Problem**: Elements may not be immediately available (AJAX, slow loading).

**Types**:

1. **Implicit Wait**: Set once, applies to all elements
   ```java
   driver.manage().timeouts().implicitlyWait(10, TimeUnit.SECONDS);
   ```
   - Waits up to specified time for element
   - Applied globally

2. **Explicit Wait**: Wait for specific condition
   ```java
   WebDriverWait wait = new WebDriverWait(driver, 10);
   WebElement element = wait.until(ExpectedConditions.presenceOfElementLocated(By.id("element")));
   ```
   - More precise
   - Waits for specific condition

3. **Fluent Wait**: Customizable wait with polling
   ```java
   Wait<WebDriver> wait = new FluentWait<>(driver)
       .withTimeout(Duration.ofSeconds(30))
       .pollingEvery(Duration.ofSeconds(5))
       .ignoring(NoSuchElementException.class);
   ```
   - Most flexible
   - Custom polling interval

**Best practice**: Use explicit waits for reliability.

---

### Screenshots

**Purpose**: Capture test state for debugging and reporting.

**Methods**:
```java
// Take screenshot
File screenshot = ((TakesScreenshot) driver).getScreenshotAs(OutputType.FILE);
FileUtils.copyFile(screenshot, new File("screenshot.png"));

// In TestNG listener
@Override
public void onTestFailure(ITestResult result) {
    TakesScreenshot ts = (TakesScreenshot) driver;
    File source = ts.getScreenshotAs(OutputType.FILE);
    // Save screenshot
}
```

**Use cases**: Failure debugging, visual verification, documentation.

---

### Headless Browser Testing

**What it is**: Running browser without GUI (faster, uses less resources).

**Chrome Headless**:
```java
ChromeOptions options = new ChromeOptions();
options.addArguments("--headless");
WebDriver driver = new ChromeDriver(options);
```

**Use cases**: CI/CD, faster execution, server environments.

**Trade-off**: Can't see what's happening, harder to debug.

---

### JavaScript Execution

**What it is**: Execute JavaScript in browser context.

**JavaScriptExecutor**:
```java
JavascriptExecutor js = (JavascriptExecutor) driver;

// Execute script
js.executeScript("return document.title");

// Scroll
js.executeScript("window.scrollTo(0, document.body.scrollHeight)");

// Click element
js.executeScript("arguments[0].click();", element);
```

**Use cases**: 
- Actions not possible with Selenium
- Scrolling
- Getting browser info
- Manipulating DOM

---

### iFrame Handling

**Challenge**: Content in nested frames requires switching context.

**Switching**:
```java
// Switch to frame
driver.switchTo().frame("frameName");
driver.switchTo().frame(0); // By index
driver.switchTo().frame(frameElement); // By element

// Switch back
driver.switchTo().defaultContent();
driver.switchTo().parentFrame();
```

**Key point**: Must switch to frame before interacting with elements inside.

---

### Maven Integration

**What Maven is**: Build and dependency management tool.

**Benefits**:
- **Dependency management**: Automatic download
- **Build lifecycle**: Compile, test, package
- **Plugins**: Extend functionality

**pom.xml structure**:
```xml
<project>
    <dependencies>
        <dependency>
            <groupId>org.seleniumhq.selenium</groupId>
            <artifactId>selenium-java</artifactId>
            <version>4.x.x</version>
        </dependency>
    </dependencies>
</project>
```

**Commands**:
- `mvn clean`: Clean build
- `mvn compile`: Compile code
- `mvn test`: Run tests
- `mvn package`: Create JAR

---

### Jenkins Integration

**What Jenkins is**: CI/CD automation server.

**Integration steps**:
1. Install Jenkins
2. Install plugins (Maven, Git, TestNG)
3. Create job
4. Configure:
   - Source code (Git)
   - Build (Maven commands)
   - Post-build (Publish test results)

**Benefits**:
- **Automated execution**: Run on schedule/trigger
- **Reports**: Test results in Jenkins
- **Notifications**: Email on failure
- **History**: Track test runs over time

---

### Exception Handling

**Common Selenium exceptions**:
- `NoSuchElementException`: Element not found
- `TimeoutException`: Wait timeout
- `StaleElementReferenceException`: Element no longer attached
- `WebDriverException`: General WebDriver error

**Handling strategy**:
```java
try {
    WebElement element = driver.findElement(By.id("element"));
    element.click();
} catch (NoSuchElementException e) {
    // Log error, take screenshot
    // Retry or fail gracefully
}
```

**Best practice**: Handle exceptions, don't let tests crash silently.

---

### Other Advanced Techniques

**Drag and Drop**:
```java
Actions actions = new Actions(driver);
actions.dragAndDrop(source, target).perform();
```

**Scroll**:
```java
JavascriptExecutor js = (JavascriptExecutor) driver;
js.executeScript("window.scrollTo(0, document.body.scrollHeight)");
```

**SSL Certificate Handling**:
```java
ChromeOptions options = new ChromeOptions();
options.setAcceptInsecureCerts(true);
```

**AJAX Handling**: Use explicit waits for AJAX-loaded content.

---

## 🎯 Key Takeaways

1. **Waits are essential** - Handle timing issues properly
2. **Screenshots aid debugging** - Capture state on failure
3. **Headless enables CI/CD** - Run without GUI
4. **JavaScript extends capabilities** - When Selenium isn't enough
5. **Maven/Jenkins enable automation** - CI/CD integration
6. **Exception handling is critical** - Robust error management

---

## 📝 Exercises

See `exercises/` folder for hands-on practice.

---

## 🔗 Connections to Other Modules

- **Module 7**: Advanced techniques build on basics
- **Module 8**: TestNG integrates with these techniques
- **Module 9**: Frameworks use these techniques
- **Module 11**: Jenkins runs these tests

---

**Reflection Question**: How do these advanced techniques transform automation from "works sometimes" to "works reliably"?

