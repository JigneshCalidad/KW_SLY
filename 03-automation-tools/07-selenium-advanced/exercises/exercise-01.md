# Exercise 1: Selenium Advanced Techniques

## Purpose

These exercises help you master Selenium's advanced techniques through hands-on practice. The goal is to develop **intuition** for when and how to use each technique, not just memorizing syntax.

---

## Exercise 1.1: Locator Strategy

### Task

Create a test for a login page. Practice using different locators:

**HTML** (imagine this is the page):
```html
<form id="loginForm">
    <input type="text" id="username" name="user" class="input-field" placeholder="Username">
    <input type="password" id="password" name="pass" class="input-field">
    <button type="submit" class="btn-primary">Login</button>
    <a href="/forgot" class="link">Forgot Password?</a>
</form>
```

**Requirements**:
1. Find username field using: ID, Name, ClassName, CSS Selector, XPath
2. Find password field using different locators
3. Find login button using different locators
4. Find "Forgot Password" link using: LinkText, PartialLinkText, XPath

**Code Example**:
```java
// Try different locators for same element
WebElement username1 = driver.findElement(By.id("username"));
WebElement username2 = driver.findElement(By.name("user"));
WebElement username3 = driver.findElement(By.cssSelector("#username"));
// etc.
```

### Reflection

- Which locator is most stable? (ID)
- When would you use CSS over XPath?
- What makes a locator "good"?

---

## Exercise 1.2: Handling Different Element Types

### Task

Create tests for a registration form with:

1. **Textbox**: Enter name, email
2. **Dropdown**: Select country
3. **Checkbox**: Accept terms and conditions
4. **Radio Button**: Select gender
5. **Button**: Submit form

**Code Structure**:
```java
// Textbox
WebElement nameField = driver.findElement(By.id("name"));
nameField.clear();
nameField.sendKeys("John Doe");

// Dropdown
Select countryDropdown = new Select(driver.findElement(By.id("country")));
countryDropdown.selectByVisibleText("USA");

// Checkbox
WebElement termsCheckbox = driver.findElement(By.id("terms"));
if (!termsCheckbox.isSelected()) {
    termsCheckbox.click();
}

// Radio Button
WebElement maleRadio = driver.findElement(By.id("male"));
maleRadio.click();

// Button
WebElement submitBtn = driver.findElement(By.id("submit"));
submitBtn.click();
```

### Reflection

- How does Selenium handle different element types?
- Why use `Select` class for dropdowns?
- What's the difference between `click()` and `isSelected()`?

---

## Exercise 1.3: Action Class - Mouse and Keyboard

### Task

1. **Mouse Hover**:
   - Find a menu item
   - Hover over it
   - Verify submenu appears

2. **Double Click**:
   - Find an element
   - Double click it
   - Verify action occurred

3. **Right Click**:
   - Right click on element
   - Verify context menu appears

4. **Drag and Drop**:
   - Find source element
   - Find target element
   - Drag source to target

**Code Example**:
```java
Actions actions = new Actions(driver);

// Hover
WebElement menu = driver.findElement(By.id("menu"));
actions.moveToElement(menu).perform();

// Double click
WebElement item = driver.findElement(By.id("item"));
actions.doubleClick(item).perform();

// Drag and drop
WebElement source = driver.findElement(By.id("source"));
WebElement target = driver.findElement(By.id("target"));
actions.dragAndDrop(source, target).perform();
```

### Reflection

- When do you need Action class vs. regular click?
- Why is `.perform()` necessary?
- What interactions can't you do with regular Selenium methods?

---

## Exercise 1.4: XPath Mastery

### Task

Practice writing XPath expressions:

**HTML Structure**:
```html
<table id="users">
    <tr>
        <th>Name</th>
        <th>Email</th>
        <th>Action</th>
    </tr>
    <tr>
        <td>Alice</td>
        <td>alice@example.com</td>
        <td><button>Edit</button></td>
    </tr>
    <tr>
        <td>Bob</td>
        <td>bob@example.com</td>
        <td><button>Edit</button></td>
    </tr>
</table>
```

**Tasks**:
1. Find table using absolute XPath (not recommended, but understand it)
2. Find table using relative XPath
3. Find "Alice" cell using text()
4. Find "Edit" button for Alice's row
5. Find all email cells
6. Find row containing "Bob" using contains()

**XPath Examples**:
```java
// Relative XPath
WebElement table = driver.findElement(By.xpath("//table[@id='users']"));

// Find by text
WebElement alice = driver.findElement(By.xpath("//td[text()='Alice']"));

// Find button in same row as Alice
WebElement editBtn = driver.findElement(By.xpath("//td[text()='Alice']/following-sibling::td/button"));

// Find all emails
List<WebElement> emails = driver.findElements(By.xpath("//table[@id='users']//td[2]"));
```

### Reflection

- When is XPath necessary vs. other locators?
- What makes XPath fragile?
- How do you write more stable XPath?

---

## Exercise 1.5: Handling Alerts and Popups

### Task

1. **Simple Alert**:
   - Trigger an alert (JavaScript: `alert("Hello")`)
   - Accept it
   - Verify it's closed

2. **Confirm Dialog**:
   - Trigger confirm (`confirm("Continue?")`)
   - Accept it
   - Dismiss it (in separate test)
   - Get text from alert

3. **Prompt Dialog**:
   - Trigger prompt (`prompt("Enter name:")`)
   - Enter text
   - Accept it

**Code Example**:
```java
// Trigger alert (via JavaScript)
JavascriptExecutor js = (JavascriptExecutor) driver;
js.executeScript("alert('Hello World');");

// Handle alert
Alert alert = driver.switchTo().alert();
String alertText = alert.getText();
System.out.println("Alert text: " + alertText);
alert.accept();
```

### Reflection

- Why must you switch to alert before interacting?
- What happens if you try to interact with page while alert is open?
- How do you handle unexpected alerts?

---

## Exercise 1.6: Working with Web Tables

### Task

Extract data from a table:

**Table Structure**:
```html
<table id="products">
    <tr>
        <th>Product</th>
        <th>Price</th>
        <th>Stock</th>
    </tr>
    <tr>
        <td>Laptop</td>
        <td>$999</td>
        <td>5</td>
    </tr>
    <tr>
        <td>Phone</td>
        <td>$699</td>
        <td>10</td>
    </tr>
</table>
```

**Tasks**:
1. Get total number of rows
2. Get total number of columns
3. Print all data from table
4. Find row with specific product (e.g., "Laptop")
5. Get price of specific product
6. Verify stock level

**Code Example**:
```java
WebElement table = driver.findElement(By.id("products"));
List<WebElement> rows = table.findElements(By.tagName("tr"));

// Iterate through rows
for (int i = 1; i < rows.size(); i++) { // Skip header
    List<WebElement> cells = rows.get(i).findElements(By.tagName("td"));
    String product = cells.get(0).getText();
    String price = cells.get(1).getText();
    String stock = cells.get(2).getText();
    System.out.println(product + " - " + price + " - " + stock);
}
```

### Reflection

- How do you navigate table structure?
- What's the relationship between table, rows, and cells?
- How would you handle dynamic tables?

---

## Exercise 1.7: Handling Dynamic Elements

### Task

1. **Wait for Element**:
   - Navigate to page with slow-loading content
   - Use explicit wait for element to appear
   - Compare with implicit wait

2. **Handle Changing IDs**:
   - Find element using stable attributes
   - Use partial matches
   - Use relative locators

3. **AJAX Content**:
   - Wait for AJAX-loaded content
   - Verify content loaded
   - Interact with dynamic content

**Code Example**:
```java
// Explicit wait
WebDriverWait wait = new WebDriverWait(driver, 10);
WebElement element = wait.until(
    ExpectedConditions.presenceOfElementLocated(By.id("dynamic"))
);

// Wait for element to be clickable
WebElement button = wait.until(
    ExpectedConditions.elementToBeClickable(By.id("button"))
);
button.click();

// Wait for text to be present
wait.until(ExpectedConditions.textToBePresentInElementLocated(
    By.id("status"), "Loaded"
));
```

### Reflection

- Why are waits necessary?
- What's the difference between implicit and explicit waits?
- How do you handle elements that may or may not appear?

---

## Exercise 1.8: Finding and Verifying Links

### Task

1. **Find All Links**:
   - Get all links on a page
   - Print their text and URLs
   - Count total links

2. **Verify Links Work**:
   - Check if link is enabled
   - Get href attribute
   - Verify link text

3. **Find Broken Links** (Conceptual):
   - How would you check if link returns 404?
   - What HTTP status codes indicate broken links?

**Code Example**:
```java
List<WebElement> links = driver.findElements(By.tagName("a"));

for (WebElement link : links) {
    String linkText = link.getText();
    String href = link.getAttribute("href");
    boolean isEnabled = link.isEnabled();
    
    System.out.println("Text: " + linkText);
    System.out.println("URL: " + href);
    System.out.println("Enabled: " + isEnabled);
}
```

### Reflection

- How do you systematically verify all links?
- What makes a link "broken"?
- How would you automate link checking?

---

## Exercise 1.9: File Upload and Download

### Task

1. **File Upload**:
   - Find file input element
   - Use sendKeys() with file path
   - Verify file uploaded

2. **File Download** (Conceptual):
   - How would you handle file downloads?
   - How do you verify file downloaded?
   - What browser settings are needed?

**Code Example**:
```java
// File upload
WebElement fileInput = driver.findElement(By.id("file-upload"));
String filePath = "/path/to/file.pdf";
fileInput.sendKeys(filePath);

// Verify upload (depends on application)
WebElement successMsg = driver.findElement(By.id("success"));
Assert.assertTrue(successMsg.isDisplayed());
```

### Reflection

- Why use sendKeys() for file upload instead of click()?
- What file paths work (absolute vs. relative)?
- How do you handle file downloads in automation?

---

## Exercise 1.10: Combining Techniques

### Task

Create a complete test scenario combining multiple techniques:

**Scenario**: Test user registration flow

1. Navigate to registration page
2. Fill form (textboxes, dropdowns, checkboxes)
3. Handle any alerts/popups
4. Submit form
5. Wait for success message
6. Verify user is registered (check table or confirmation)

**Requirements**:
- Use appropriate locators
- Handle dynamic content (waits)
- Verify results
- Handle errors gracefully

### Reflection

- How do techniques work together?
- What makes a test "complete"?
- How do you structure a complex test?

---

## 🎯 Self-Assessment

After completing these exercises, ask yourself:

1. Can I choose the right locator for each situation?
2. Do I understand when to use Action class?
3. Can I write effective XPath expressions?
4. Can I handle alerts, tables, and dynamic content?
5. Can I combine techniques for complex scenarios?

---

## 💡 Key Insights to Carry Forward

- **Locator strategy matters** - Choose stable, reliable locators
- **Different elements need different approaches** - Textbox vs. dropdown vs. checkbox
- **Waits are essential** - Handle timing issues properly
- **XPath is powerful but fragile** - Use when simpler locators fail
- **Techniques combine** - Real tests use multiple techniques

---

**Next Steps**: Once comfortable with these techniques, move to Module 8: TestNG to organize these into proper test frameworks.

