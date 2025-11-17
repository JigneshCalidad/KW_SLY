# Module 7: Selenium Advanced

## 🌱 Why This Module Matters

This module covers the **practical techniques** you'll use daily in Selenium automation. These aren't just methods to memorize—they're **patterns for interacting with web elements** and handling the complexities of web applications.

Understanding these techniques enables you to:
- Locate elements reliably (the foundation of automation)
- Interact with different element types
- Handle dynamic content and waits
- Deal with complex UI components (tables, alerts, frames)

---

## 📚 Learning Objectives

By the end of this module, you will understand:

1. **Locators** - Finding elements on the page
2. **WebElement Interactions** - Clicking, typing, selecting
3. **Action Class** - Advanced mouse and keyboard actions
4. **File Operations** - Upload and download
5. **XPath** - Powerful element location
6. **Alert Handling** - Popups and dialogs
7. **Web Tables** - Working with table data
8. **Dynamic Elements** - Handling changing content
9. **Links** - Finding and verifying links

---

## 🧩 Conceptual Overview

### Locators in Selenium

**What they are**: Ways to **identify elements** on a web page.

**Types**:
1. **ID**: Unique identifier (fastest, most reliable)
2. **Name**: Name attribute
3. **ClassName**: CSS class
4. **TagName**: HTML tag
5. **LinkText**: Exact link text
6. **PartialLinkText**: Partial link text
7. **CSS Selector**: CSS path
8. **XPath**: XML path

**Principle**: Use the **most stable** locator. ID > Name > CSS > XPath (generally).

**Example**:
```java
driver.findElement(By.id("username"));
driver.findElement(By.name("email"));
driver.findElement(By.cssSelector(".login-button"));
driver.findElement(By.xpath("//input[@type='text']"));
```

---

### FindElement vs FindElements

**findElement()**:
- Returns **first matching element**
- Throws exception if not found
- Returns `WebElement`

**findElements()**:
- Returns **list of all matching elements**
- Returns empty list if not found
- Returns `List<WebElement>`

**Use case**: Use `findElements()` when you need multiple elements or to check existence.

---

### WebElement Interactions

**Basic interactions**:

1. **Click**: `element.click()`
2. **Send Keys**: `element.sendKeys("text")`
3. **Clear**: `element.clear()`
4. **Get Text**: `element.getText()`
5. **Get Attribute**: `element.getAttribute("href")`
6. **Is Displayed**: `element.isDisplayed()`
7. **Is Enabled**: `element.isEnabled()`
8. **Is Selected**: `element.isSelected()`

**Example**:
```java
WebElement username = driver.findElement(By.id("username"));
username.clear();
username.sendKeys("testuser");
WebElement loginBtn = driver.findElement(By.id("login"));
loginBtn.click();
```

---

### Form Elements

**Textbox**: `sendKeys()`, `clear()`
**Button**: `click()`
**Checkbox**: `click()` to select/deselect, `isSelected()` to check
**Radio Button**: `click()` to select
**Dropdown**: Use `Select` class

**Dropdown Example**:
```java
Select dropdown = new Select(driver.findElement(By.id("country")));
dropdown.selectByVisibleText("USA");
dropdown.selectByValue("us");
dropdown.selectByIndex(0);
```

---

### Action Class

**What it is**: Advanced interactions (mouse, keyboard, drag-drop).

**Common actions**:
- **Mouse Hover**: `actions.moveToElement(element).perform()`
- **Double Click**: `actions.doubleClick(element).perform()`
- **Right Click**: `actions.contextClick(element).perform()`
- **Drag and Drop**: `actions.dragAndDrop(source, target).perform()`
- **Key Press**: `actions.sendKeys(Keys.ENTER).perform()`

**Example**:
```java
Actions actions = new Actions(driver);
actions.moveToElement(menu).perform();
actions.dragAndDrop(source, target).perform();
```

---

### File Upload/Download

**Upload**:
```java
WebElement fileInput = driver.findElement(By.id("file"));
fileInput.sendKeys("/path/to/file.pdf");
```

**Download**: Configure browser preferences, then click download link.

---

### XPath

**What it is**: Powerful language for locating elements.

**Types**:
- **Absolute**: Full path from root (`/html/body/div/input`)
- **Relative**: Path from anywhere (`//input[@id='username']`)

**Axes** (relationships):
- `//`: Anywhere
- `/`: Direct child
- `..`: Parent
- `following-sibling`: Next siblings
- `preceding-sibling`: Previous siblings
- `ancestor`: All ancestors
- `descendant`: All descendants

**Functions**:
- `text()`: Element text
- `contains()`: Partial match
- `starts-with()`: Prefix match

**Example**:
```java
// Element with specific text
driver.findElement(By.xpath("//button[text()='Submit']"));

// Element containing text
driver.findElement(By.xpath("//div[contains(text(), 'Welcome')]"));

// Element with attribute
driver.findElement(By.xpath("//input[@type='text']"));

// Following sibling
driver.findElement(By.xpath("//label[text()='Email']/following-sibling::input"));
```

**Use wisely**: XPath can be fragile. Prefer simpler locators when possible.

---

### Alert & Popup Handling

**Types**:
- **Alert**: Simple message (OK button)
- **Confirm**: OK/Cancel
- **Prompt**: Input field

**Handling**:
```java
Alert alert = driver.switchTo().alert();
alert.accept();  // Click OK
alert.dismiss(); // Click Cancel
String text = alert.getText(); // Get message
alert.sendKeys("input"); // For prompt
```

**Key point**: Must switch to alert before interacting.

---

### Web Table Handling

**Challenges**: Tables are complex HTML structures.

**Approaches**:
1. **Find table**: `WebElement table = driver.findElement(By.id("table"))`
2. **Find rows**: `List<WebElement> rows = table.findElements(By.tagName("tr"))`
3. **Find cells**: `List<WebElement> cells = row.findElements(By.tagName("td"))`
4. **Extract data**: Iterate and get text

**Example**:
```java
WebElement table = driver.findElement(By.id("users"));
List<WebElement> rows = table.findElements(By.tagName("tr"));
for (WebElement row : rows) {
    List<WebElement> cells = row.findElements(By.tagName("td"));
    String name = cells.get(0).getText();
    String email = cells.get(1).getText();
}
```

**Dynamic tables**: Use XPath with dynamic data.

---

### Dynamic Elements

**Challenge**: Elements that change (IDs, content, timing).

**Strategies**:
- Use **stable attributes** (data attributes, partial text)
- Use **relative locators** (near other stable elements)
- Use **waits** (wait for element to appear)
- Use **findElements()** to check existence

**Example**:
```java
// Wait for element
WebDriverWait wait = new WebDriverWait(driver, 10);
WebElement element = wait.until(ExpectedConditions.presenceOfElementLocated(By.id("dynamic")));
```

---

### Finding Links

**Methods**:
- **LinkText**: Exact match
- **PartialLinkText**: Partial match
- **XPath with text()**: Flexible matching

**Verify links**:
```java
List<WebElement> links = driver.findElements(By.tagName("a"));
for (WebElement link : links) {
    String href = link.getAttribute("href");
    // Verify link is valid
}
```

**Broken links**: Check HTTP response codes.

---

## 🎯 Key Takeaways

1. **Locators are foundational** - Choose stable, reliable locators
2. **Multiple interaction methods** - Click, type, select, hover
3. **XPath is powerful but fragile** - Use when simpler locators fail
4. **Dynamic content requires waits** - Elements may not be immediately available
5. **Complex elements need special handling** - Tables, alerts, frames

---

## 📝 Exercises

See `exercises/` folder for hands-on practice.

---

## 🔗 Connections to Other Modules

- **Module 6**: Builds on Selenium basics
- **Module 8**: TestNG organizes these techniques into tests
- **Module 9**: Frameworks structure these interactions

---

**Reflection Question**: How do you balance using powerful locators (XPath) with maintaining stable, maintainable test code?

