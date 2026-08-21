# Selenium — Complete QA Automation Notes

## 1. What is Selenium?

**Selenium** is an open-source framework used to automate web browsers and perform automated testing of web applications.

For QA Automation, Selenium is commonly used with:

- Java
- TestNG / JUnit
- Maven
- Cucumber BDD
- Jenkins
- Git
- Page Object Model (POM)

Typical flow:

```text
Java Program
    ↓
Selenium WebDriver
    ↓
Browser Driver / WebDriver implementation
    ↓
Chrome / Firefox / Edge
    ↓
Web Application
```

---

## 2. Selenium Components

### Selenium WebDriver

The most commonly used Selenium component.

It provides APIs to:

- Launch browsers
- Open URLs
- Locate web elements
- Enter text
- Click buttons
- Select dropdowns
- Handle alerts
- Manage windows/tabs
- Take screenshots
- Execute JavaScript

### Selenium IDE

A browser-based record-and-playback tool.

Useful for:

- Learning Selenium
- Quick prototypes
- Simple test cases

For enterprise automation, WebDriver is generally more flexible.

### Selenium Grid

Used to execute tests across:

- Multiple browsers
- Multiple operating systems
- Multiple machines

Example:

```text
Test Suite
    ↓
Selenium Grid
    ├── Chrome / Windows
    ├── Firefox / Windows
    ├── Edge / Windows
    └── Chrome / Linux
```

---

## 3. Selenium WebDriver Architecture

Modern Selenium communication can be understood as:

```text
Automation Code
      ↓
Selenium WebDriver API
      ↓
Browser Driver / WebDriver implementation
      ↓
Browser
```

Example:

```java
WebDriver driver = new ChromeDriver();
```

This creates a Chrome browser session.

---

## 4. Basic Selenium Program

```java
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;

public class BasicSelenium {
    public static void main(String[] args) {

        WebDriver driver = new ChromeDriver();

        driver.get("https://www.google.com");

        System.out.println(driver.getTitle());

        driver.quit();
    }
}
```

### Explanation

```java
WebDriver driver = new ChromeDriver();
```

Creates a Chrome browser instance.

```java
driver.get("https://www.google.com");
```

Navigates to the specified URL.

```java
driver.getTitle();
```

Returns the page title.

```java
driver.quit();
```

Closes the browser and ends the WebDriver session.

---

## 5. Important WebDriver Methods

### `get()`

```java
driver.get("https://example.com");
```

Opens a URL.

### `getTitle()`

```java
String title = driver.getTitle();
```

Returns the page title.

### `getCurrentUrl()`

```java
String url = driver.getCurrentUrl();
```

Returns the current URL.

### `getPageSource()`

```java
String source = driver.getPageSource();
```

Returns the page source.

### `close()`

```java
driver.close();
```

Closes the current browser window.

### `quit()`

```java
driver.quit();
```

Closes all browser windows and ends the WebDriver session.

### Interview Point

`close()` closes the current window, whereas `quit()` terminates the entire WebDriver session.

---

## 6. Locators

Locators are used to identify elements on a web page.

Selenium supports:

1. ID
2. Name
3. Class Name
4. Tag Name
5. Link Text
6. Partial Link Text
7. CSS Selector
8. XPath

Example HTML:

```html
<input id="username" name="user" class="login-field">
```

### ID

```java
driver.findElement(By.id("username"));
```

### Name

```java
driver.findElement(By.name("user"));
```

### Class Name

```java
driver.findElement(By.className("login-field"));
```

### Tag Name

```java
driver.findElement(By.tagName("input"));
```

### CSS Selector

```java
driver.findElement(By.cssSelector("#username"));
```

### XPath

```java
driver.findElement(By.xpath("//input[@id='username']"));
```

---

## 7. Finding Web Elements

```java
WebElement username =
        driver.findElement(By.id("username"));
```

Then interact with it:

```java
username.sendKeys("admin");
```

```java
username.click();
```

```java
username.clear();
```

---

## 8. Common WebElement Methods

### `click()`

```java
element.click();
```

Clicks an element.

### `sendKeys()`

```java
element.sendKeys("Selenium");
```

Enters text.

### `clear()`

```java
element.clear();
```

Clears text.

### `getText()`

```java
String text = element.getText();
```

Returns visible text.

### `getAttribute()`

```java
String value = element.getAttribute("value");
```

Returns an HTML attribute value.

### `isDisplayed()`

```java
element.isDisplayed();
```

Checks whether the element is visible.

### `isEnabled()`

```java
element.isEnabled();
```

Checks whether the element is enabled.

### `isSelected()`

```java
element.isSelected();
```

Checks whether a checkbox or radio option is selected.

---

## 9. Example Login Automation

```java
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;

public class LoginTest {

    public static void main(String[] args) {

        WebDriver driver = new ChromeDriver();

        driver.get("https://example.com/login");

        driver.findElement(By.id("username"))
                .sendKeys("admin");

        driver.findElement(By.id("password"))
                .sendKeys("admin123");

        driver.findElement(By.id("login"))
                .click();

        driver.quit();
    }
}
```

---

## 10. XPath

XPath is one of the most commonly used locator strategies in Selenium.

### Absolute XPath

```xpath
/html/body/div/input
```

Generally avoid this because it is fragile.

### Relative XPath

```xpath
//input[@id='username']
```

Better and more maintainable.

### XPath with Text

```xpath
//button[text()='Login']
```

### Contains

```xpath
//input[contains(@id,'user')]
```

### Starts With

```xpath
//input[starts-with(@id,'user')]
```

### Multiple Attributes

```xpath
//input[@type='text' and @name='username']
```

---

## 11. CSS Selectors

### ID Selector

```css
#username
```

### Class Selector

```css
.username
```

### Attribute Selector

```css
input[name='username']
```

### Multiple Attributes

```css
input[type='text'][name='username']
```

---

## 12. Browser Navigation

```java
driver.get("https://google.com");
```

```java
driver.navigate().to("https://google.com");
```

```java
driver.navigate().back();
```

```java
driver.navigate().forward();
```

```java
driver.navigate().refresh();
```

---

## 13. Browser Window Management

```java
driver.manage().window().maximize();
```

```java
driver.manage().window().minimize();
```

```java
driver.manage().window().fullscreen();
```

---

## 14. Handling Alerts

### Accept Alert

```java
Alert alert = driver.switchTo().alert();
alert.accept();
```

### Dismiss Alert

```java
alert.dismiss();
```

### Get Alert Text

```java
String message = alert.getText();
```

### Enter Text into Prompt

```java
alert.sendKeys("Selenium");
```

---

## 15. Handling Frames

### Switch to Frame by Name or ID

```java
driver.switchTo().frame("frameName");
```

### Switch Using WebElement

```java
WebElement frame =
        driver.findElement(By.id("frame"));

driver.switchTo().frame(frame);
```

### Return to Main Document

```java
driver.switchTo().defaultContent();
```

### Return to Parent Frame

```java
driver.switchTo().parentFrame();
```

---

## 16. Handling Multiple Windows/Tabs

Get all window handles:

```java
Set<String> windows = driver.getWindowHandles();
```

Switch to a window:

```java
for (String window : windows) {
    driver.switchTo().window(window);
}
```

A better approach in framework code is to store handles and switch deliberately based on the required window.

---

## 17. Dropdown Handling

For standard HTML `<select>` dropdowns:

```java
Select select =
        new Select(driver.findElement(By.id("country")));
```

### Select by Visible Text

```java
select.selectByVisibleText("India");
```

### Select by Value

```java
select.selectByValue("IN");
```

### Select by Index

```java
select.selectByIndex(2);
```

---

## 18. Mouse Actions

Using `Actions`:

```java
Actions actions = new Actions(driver);
```

### Mouse Hover

```java
actions.moveToElement(element).perform();
```

### Double Click

```java
actions.doubleClick(element).perform();
```

### Right Click

```java
actions.contextClick(element).perform();
```

### Drag and Drop

```java
actions.dragAndDrop(source, target).perform();
```

---

## 19. Keyboard Actions

```java
actions.sendKeys(Keys.ENTER).perform();
```

Example:

```java
element.sendKeys(Keys.CONTROL, "a");
```

---

## 20. Waits

Synchronization is one of the most important Selenium concepts.

### Implicit Wait

```java
driver.manage().timeouts()
        .implicitlyWait(Duration.ofSeconds(10));
```

Selenium waits up to the specified time when locating elements.

### Explicit Wait

```java
WebDriverWait wait =
        new WebDriverWait(driver, Duration.ofSeconds(10));

WebElement element = wait.until(
        ExpectedConditions.visibilityOfElementLocated(
                By.id("username")
        )
);
```

Explicit waits are preferred for specific synchronization conditions.

### Common Expected Conditions

```java
ExpectedConditions.visibilityOfElementLocated(...)
```

```java
ExpectedConditions.elementToBeClickable(...)
```

```java
ExpectedConditions.presenceOfElementLocated(...)
```

```java
ExpectedConditions.urlContains(...)
```

```java
ExpectedConditions.titleContains(...)
```

### Thread.sleep()

```java
Thread.sleep(5000);
```

This is a hard wait and should generally be avoided in production automation because it pauses execution for a fixed duration regardless of whether the element is ready.

---

## 21. Screenshots

```java
TakesScreenshot screenshot =
        (TakesScreenshot) driver;

File source =
        screenshot.getScreenshotAs(OutputType.FILE);
```

Screenshots are commonly captured when a test fails.

---

## 22. JavaScriptExecutor

Used when normal Selenium interaction is insufficient.

```java
JavascriptExecutor js =
        (JavascriptExecutor) driver;
```

### Scroll

```java
js.executeScript(
        "window.scrollBy(0,500)"
);
```

### Click

```java
js.executeScript(
        "arguments[0].click();",
        element
);
```

JavaScript should be used carefully; normal Selenium interactions are usually preferable when they work reliably.

---

## 23. Selenium with TestNG

Example:

```java
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
import org.testng.annotations.AfterMethod;
import org.testng.annotations.BeforeMethod;
import org.testng.annotations.Test;

public class LoginTest {

    WebDriver driver;

    @BeforeMethod
    public void setUp() {
        driver = new ChromeDriver();
        driver.get("https://example.com");
    }

    @Test
    public void loginTest() {
        System.out.println(driver.getTitle());
    }

    @AfterMethod
    public void tearDown() {
        driver.quit();
    }
}
```

Typical structure:

```text
@BeforeMethod
      ↓
@Test
      ↓
@AfterMethod
```

---

## 24. Page Object Model (POM)

**Page Object Model** is a design pattern widely used in Selenium automation frameworks.

Instead of putting locators and actions directly inside test classes, they are maintained inside page classes.

### LoginPage.java

```java
public class LoginPage {

    WebDriver driver;

    By username = By.id("username");
    By password = By.id("password");
    By loginButton = By.id("login");

    public LoginPage(WebDriver driver) {
        this.driver = driver;
    }

    public void enterUsername(String value) {
        driver.findElement(username).sendKeys(value);
    }

    public void enterPassword(String value) {
        driver.findElement(password).sendKeys(value);
    }

    public void clickLogin() {
        driver.findElement(loginButton).click();
    }
}
```

### Test Class

```java
LoginPage loginPage = new LoginPage(driver);

loginPage.enterUsername("admin");
loginPage.enterPassword("admin123");
loginPage.clickLogin();
```

### Advantages of POM

- Better maintainability
- Reusable page actions
- Centralized locators
- Cleaner test classes
- Easier updates when UI changes

---

## 25. Typical Selenium Automation Framework

```text
Automation Framework
│
├── src/test/java
│   ├── tests
│   ├── pages
│   ├── utilities
│   ├── base
│   └── listeners
│
├── src/test/resources
│   ├── testdata
│   └── config
│
├── pom.xml
└── testng.xml
```

Common technologies:

```text
Selenium
Java
TestNG
Maven
Cucumber
POM
Jenkins
Git
JIRA
```

---

## 26. Selenium Interview Questions

### What is Selenium?

Selenium is an open-source framework for automating web browsers and testing web applications.

### Selenium WebDriver vs Selenium IDE?

**WebDriver:** Programmatic browser automation.

**IDE:** Record-and-playback browser extension.

### `close()` vs `quit()`?

`close()` closes the current browser window.

`quit()` closes all browser windows and terminates the WebDriver session.

### Implicit Wait vs Explicit Wait?

**Implicit Wait:** Global wait for element location.

**Explicit Wait:** Waits for a specific condition.

### XPath vs CSS Selector?

XPath supports powerful DOM traversal and text-based expressions. CSS selectors are often concise and easy to read for straightforward element selection.

### Why use Page Object Model?

POM separates page locators/actions from test logic, improving maintainability, reusability, and readability.

### Can Selenium automate desktop applications?

No. Selenium is designed primarily for web browser automation.

### Can Selenium handle API testing?

Selenium itself is not an API testing tool. Tools such as REST Assured and Postman are commonly used for API testing.

---

## 27. Selenium + Java QA Automation Roadmap

```text
Java Basics
     ↓
OOP Concepts
     ↓
Selenium WebDriver
     ↓
Locators
     ↓
XPath / CSS
     ↓
WebElement
     ↓
Waits
     ↓
Alerts / Frames / Windows
     ↓
Actions / Dropdowns
     ↓
JavaScriptExecutor
     ↓
TestNG
     ↓
Page Object Model
     ↓
Maven
     ↓
Cucumber BDD
     ↓
Git
     ↓
Jenkins CI/CD
     ↓
Enterprise Automation Framework
```

---

## 28. High-Priority Interview Topics

For a QA Automation / SDET interview, focus especially on:

1. Selenium WebDriver architecture
2. Locators
3. XPath
4. CSS Selectors
5. WebElement methods
6. Implicit vs Explicit Waits
7. Fluent Wait
8. Alerts
9. Frames
10. Multiple windows and tabs
11. Dropdowns
12. Actions class
13. JavaScriptExecutor
14. Screenshots
15. Page Object Model
16. TestNG
17. Maven
18. Data-driven testing
19. Cucumber BDD
20. CI/CD integration with Jenkins

---

## 29. Useful Imports

A common Selenium Java test may require imports such as:

```java
import java.io.File;
import java.time.Duration;
import java.util.Set;

import org.openqa.selenium.Alert;
import org.openqa.selenium.By;
import org.openqa.selenium.Keys;
import org.openqa.selenium.OutputType;
import org.openqa.selenium.TakesScreenshot;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.JavascriptExecutor;

import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.interactions.Actions;
import org.openqa.selenium.support.ui.ExpectedConditions;
import org.openqa.selenium.support.ui.Select;
import org.openqa.selenium.support.ui.WebDriverWait;
```

---

## 30. Final Summary

Selenium is a core technology for web automation. To become strong in Selenium-based QA automation, understand the complete path from browser control to framework design:

```text
Java
  ↓
Selenium WebDriver
  ↓
Locators
  ↓
WebElement Operations
  ↓
Synchronization
  ↓
Browser Interactions
  ↓
TestNG
  ↓
POM
  ↓
Maven
  ↓
Cucumber
  ↓
Jenkins
  ↓
Enterprise Automation Framework
```

The most important practical skill is not just writing Selenium commands, but designing **stable, maintainable, reusable, and scalable automation**.
