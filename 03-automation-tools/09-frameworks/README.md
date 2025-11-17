# Module 9: Automation Frameworks

## 🌱 Why This Module Matters

A framework isn't just code organization—it's a **systematic approach** to test automation. Frameworks provide:
- **Structure**: How tests are organized
- **Reusability**: Common code shared across tests
- **Maintainability**: Changes in one place affect all tests
- **Scalability**: Easy to add new tests

Understanding frameworks transforms you from writing scripts to **building test systems**.

---

## 📚 Learning Objectives

By the end of this module, you will understand:

1. **Page Object Model (POM)** - Organizing page interactions
2. **Page Factory** - Simplifying POM
3. **Data-Driven Testing** - Testing with different data
4. **Keyword-Driven Testing** - Tests as keywords
5. **Hybrid Framework** - Combining approaches
6. **Excel Integration** - Reading test data
7. **Date Picker Handling** - Complex UI components

---

## 🧩 Conceptual Overview

### Page Object Model (POM)

**What it is**: Design pattern that models web pages as objects.

**Concept**: Each page is a class. Page elements are properties. Page actions are methods.

**Benefits**:
- **Separation of concerns**: Page logic separate from test logic
- **Reusability**: Page methods used by multiple tests
- **Maintainability**: UI changes affect one class
- **Readability**: Tests read like user stories

**Structure**:
```java
public class LoginPage {
    // Elements
    private WebElement username;
    private WebElement password;
    private WebElement loginButton;
    
    // Actions
    public void enterUsername(String user) {
        username.sendKeys(user);
    }
    
    public void enterPassword(String pass) {
        password.sendKeys(pass);
    }
    
    public void clickLogin() {
        loginButton.click();
    }
    
    public void login(String user, String pass) {
        enterUsername(user);
        enterPassword(pass);
        clickLogin();
    }
}
```

**Test uses page**:
```java
@Test
public void loginTest() {
    LoginPage loginPage = new LoginPage(driver);
    loginPage.login("user", "pass");
}
```

**Principle**: Tests should read like **what user does**, not **how Selenium does it**.

---

### Page Factory

**What it is**: TestNG feature that simplifies POM initialization.

**How it works**: Uses `@FindBy` annotations and `PageFactory.initElements()`.

**Example**:
```java
public class LoginPage {
    @FindBy(id = "username")
    private WebElement username;
    
    @FindBy(id = "password")
    private WebElement password;
    
    @FindBy(id = "login")
    private WebElement loginButton;
    
    public LoginPage(WebDriver driver) {
        PageFactory.initElements(driver, this);
    }
    
    public void login(String user, String pass) {
        username.sendKeys(user);
        password.sendKeys(pass);
        loginButton.click();
    }
}
```

**Benefits**: Less boilerplate, cleaner code.

---

### Data-Driven Testing

**What it is**: Running same test with different data.

**Approaches**:
1. **TestNG DataProvider**: Annotated method provides data
2. **Excel files**: Read from spreadsheet
3. **CSV files**: Comma-separated values
4. **JSON files**: Structured data
5. **Database**: Query for test data

**DataProvider Example**:
```java
@DataProvider(name = "loginData")
public Object[][] getLoginData() {
    return new Object[][] {
        {"user1", "pass1"},
        {"user2", "pass2"},
        {"user3", "pass3"}
    };
}

@Test(dataProvider = "loginData")
public void loginTest(String username, String password) {
    loginPage.login(username, password);
}
```

**Benefits**: One test, multiple scenarios.

---

### Excel Integration

**Reading from Excel** (Apache POI):

```java
FileInputStream file = new FileInputStream("testdata.xlsx");
Workbook workbook = new XSSFWorkbook(file);
Sheet sheet = workbook.getSheet("LoginData");

for (Row row : sheet) {
    String username = row.getCell(0).getStringCellValue();
    String password = row.getCell(1).getStringCellValue();
    // Use data in test
}
```

**Use case**: Business users can maintain test data in Excel.

---

### Keyword-Driven Testing

**What it is**: Tests written as keywords (actions).

**Concept**: Tests are sequences of keywords. Keywords map to code.

**Example keywords**:
- `OPEN_BROWSER`
- `NAVIGATE_TO_URL`
- `ENTER_TEXT`
- `CLICK_BUTTON`
- `VERIFY_TEXT`

**Benefits**:
- Non-technical users can write tests
- Tests are readable
- Keywords reusable

**Implementation**: Map keywords to methods, execute sequence.

---

### Hybrid Framework

**What it is**: Combines multiple approaches.

**Typical combination**:
- **POM**: Page organization
- **Data-Driven**: Test data externalized
- **Keyword-Driven**: Some keyword support
- **TestNG**: Test execution

**Benefits**: Leverage strengths of each approach.

---

### Date Picker Handling

**Challenge**: Date pickers are complex UI components.

**Approaches**:
1. **Direct input**: `sendKeys()` with formatted date
2. **JavaScript**: Execute JS to set date
3. **Click navigation**: Click through calendar
4. **Library**: Use date picker library methods

**Example**:
```java
// Direct input
dateField.sendKeys("12/25/2023");

// JavaScript
JavascriptExecutor js = (JavascriptExecutor) driver;
js.executeScript("document.getElementById('date').value='12/25/2023'");
```

---

## 🎯 Key Takeaways

1. **POM organizes page interactions** - Pages as objects, actions as methods
2. **Data-driven enables scalability** - One test, many scenarios
3. **Frameworks provide structure** - Systematic approach to automation
4. **Choose framework wisely** - Match to project needs
5. **Maintainability matters** - Framework should reduce maintenance

---

## 📝 Exercises

See `exercises/` folder for hands-on practice.

---

## 🔗 Connections to Other Modules

- **Module 7**: Frameworks use Selenium techniques
- **Module 8**: TestNG executes framework tests
- **Module 10**: Advanced techniques enhance frameworks

---

**Reflection Question**: How does a framework change your relationship with test code—from writing scripts to building systems?

