# Exercise 1: Selenium Introduction

## Purpose

These exercises help you set up Selenium and write your first automation script, understanding the fundamentals of browser automation.

---

## Exercise 1.1: Environment Setup

### Task

1. **Verify Java Installation**:
   ```bash
   java -version
   javac -version
   ```
   - Ensure JDK is installed (not just JRE)
   - Note the version

2. **Choose an IDE**:
   - Eclipse, IntelliJ IDEA, or VS Code
   - Set up a new Java project

3. **Add Selenium Dependency**:
   - **Option A (Maven - Recommended)**:
     - Create Maven project
     - Add Selenium dependency to `pom.xml`
   - **Option B (Manual)**:
     - Download Selenium JARs
     - Add to project classpath

4. **Download Browser Driver**:
   - Download ChromeDriver (match your Chrome version)
   - Place in project folder or add to PATH

### Reflection
- Why is it important to match driver version with browser version?
- What's the advantage of using Maven over manual JAR management?

---

## Exercise 1.2: First Selenium Script

### Task

Write a simple script that:

1. Opens a browser (Chrome)
2. Navigates to a website (e.g., https://www.example.com)
3. Gets and prints the page title
4. Closes the browser

### Starter Code
```java
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;

public class FirstSeleniumTest {
    public static void main(String[] args) {
        // Set driver path (if not in PATH)
        System.setProperty("webdriver.chrome.driver", "path/to/chromedriver");
        
        // Create WebDriver instance
        WebDriver driver = new ChromeDriver();
        
        // Your code here
        
        // Close browser
        driver.quit();
    }
}
```

### Expected Output
```
Page title: Example Domain
```

### Reflection
- What happens if you use `driver.close()` instead of `driver.quit()`?
- Why is it important to always close the browser?

---

## Exercise 1.3: Understanding WebDriver

### Task

1. **Create WebDriver instances for different browsers**:
   - Chrome
   - Firefox (if available)
   - Edge (if available)

2. **Observe the pattern**:
   - How are they created?
   - What's the same? What's different?

3. **Answer**:
   - What is WebDriver? (Interface or class?)
   - Why do we use interfaces?

### Reflection
- How does using an interface make your code more flexible?
- What would happen if WebDriver was a concrete class instead of an interface?

---

## Exercise 1.4: Basic Browser Operations

### Task

Write a script that demonstrates:

1. **Navigate**:
   - `driver.get(url)` - Navigate to URL
   - `driver.navigate().to(url)` - Alternative navigation
   - `driver.navigate().back()` - Go back
   - `driver.navigate().forward()` - Go forward
   - `driver.navigate().refresh()` - Refresh page

2. **Get Information**:
   - `driver.getTitle()` - Page title
   - `driver.getCurrentUrl()` - Current URL
   - `driver.getPageSource()` - Page source (first 100 characters)

3. **Window Management**:
   - `driver.manage().window().maximize()` - Maximize window
   - `driver.manage().window().getSize()` - Get window size

### Reflection
- When would you use `navigate().to()` vs `get()`?
- Why might you want to maximize the window in tests?

---

## Exercise 1.5: Error Handling

### Task

1. **Write code that causes errors**:
   - Navigate to invalid URL
   - Try to get title after closing browser
   - Use wrong driver path

2. **Observe error messages**:
   - What information do they provide?
   - How can you use this for debugging?

3. **Add basic error handling**:
   ```java
   try {
       // Selenium code
   } catch (Exception e) {
       System.out.println("Error: " + e.getMessage());
   }
   ```

### Reflection
- Why is error handling important in automation?
- How do error messages help you debug?

---

## Exercise 1.6: Automation vs Manual Testing

### Task (Conceptual)

Think about a simple manual test (e.g., login to a website). Answer:

1. **Manual Steps**:
   - List each step you'd do manually
   - How long would it take?

2. **Automation Steps**:
   - How would you automate each step?
   - What challenges might you face?

3. **Comparison**:
   - When is automation faster?
   - When is manual testing better?
   - What's the initial investment for automation?

### Reflection
- What makes a test "worth automating"?
- How does automation change your testing approach?

---

## 🎯 Self-Assessment

After completing these exercises, ask yourself:

1. Can I set up Selenium in my environment?
2. Can I write a basic script that opens a browser and navigates?
3. Do I understand what WebDriver is?
4. Can I handle basic browser operations?
5. Do I understand when to automate vs. test manually?

---

## 💡 Key Insights to Carry Forward

- **Setup matters**: Proper environment setup prevents many issues
- **WebDriver is an interface**: Different implementations for different browsers
- **Always close browsers**: Use `quit()` to clean up resources
- **Error handling**: Helps debugging and makes scripts robust
- **Automation is a tool**: Use it wisely, not everywhere

---

**Next Steps**: Once comfortable with basics, move to Module 7: Selenium Advanced for locators and interactions.

