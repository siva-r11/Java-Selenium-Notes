# Java Class, Object, and Method — Selenium Example

## 1. Basic Concepts

In Java, **class, object, and method** are fundamental OOP concepts.

- **Class** → Blueprint or template
- **Object** → Instance of a class
- **Method** → Performs a specific action

---

## 2. Selenium Example

```java
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;

public class LoginTest {

    public static void main(String[] args) {

        // Creating an object of ChromeDriver
        WebDriver driver = new ChromeDriver();

        // Calling a method
        driver.get("https://www.google.com");

        // Calling another method
        String title = driver.getTitle();

        System.out.println("Page Title: " + title);

        // Calling quit() method
        driver.quit();
    }
}
```

---

## 3. Class

A **class** is a blueprint or template that contains variables and methods.

```java
public class LoginTest {

}
```

Here:

- `LoginTest` → Class
- It contains the Selenium automation code.

Selenium also provides classes such as:

```java
ChromeDriver
```

---

## 4. Object

An **object** is an instance of a class.

```java
WebDriver driver = new ChromeDriver();
```

Here:

- `WebDriver` → Interface/reference type
- `driver` → Reference variable
- `new ChromeDriver()` → Creates a browser/WebDriver object

The `driver` object represents the browser session.

---

## 5. Method

A **method** performs a specific action.

### `get()`

```java
driver.get("https://www.google.com");
```

Opens the specified URL.

### `getTitle()`

```java
String title = driver.getTitle();
```

Returns the current page title.

### `quit()`

```java
driver.quit();
```

Closes all browser windows and ends the WebDriver session.

---

# Selenium + Page Object Model Example

Page Object Model (POM) is commonly used in Selenium automation frameworks.

## LoginPage.java

```java
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;

public class LoginPage {

    WebDriver driver;

    // Constructor
    public LoginPage(WebDriver driver) {
        this.driver = driver;
    }

    // Method
    public void enterUsername(String username) {
        driver.findElement(By.id("username")).sendKeys(username);
    }

    // Method
    public void enterPassword(String password) {
        driver.findElement(By.id("password")).sendKeys(password);
    }

    // Method
    public void clickLogin() {
        driver.findElement(By.id("login")).click();
    }
}
```

## LoginTest.java

```java
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;

public class LoginTest {

    public static void main(String[] args) {

        // Creating WebDriver object
        WebDriver driver = new ChromeDriver();

        driver.get("https://example.com/login");

        // Creating LoginPage object
        LoginPage loginPage = new LoginPage(driver);

        // Calling methods using the object
        loginPage.enterUsername("siva");
        loginPage.enterPassword("password123");
        loginPage.clickLogin();

        driver.quit();
    }
}
```

---

# Understanding the POM Example

## Class

```java
public class LoginPage
```

`LoginPage` is a **class**.

It contains:

- WebDriver
- Constructor
- Login page actions
- Selenium methods

---

## Object

```java
LoginPage loginPage = new LoginPage(driver);
```

`loginPage` is an **object/reference** of the `LoginPage` class.

The object allows us to access the methods inside `LoginPage`.

---

## Constructor

```java
public LoginPage(WebDriver driver) {
    this.driver = driver;
}
```

The constructor initializes the `WebDriver` for the `LoginPage` object.

When this statement executes:

```java
LoginPage loginPage = new LoginPage(driver);
```

the constructor is called automatically.

---

## Methods

```java
enterUsername()
enterPassword()
clickLogin()
```

These are methods defined in the `LoginPage` class.

For example:

```java
loginPage.enterUsername("siva");
```

The `enterUsername()` method performs the username entry action.

---

# Quick Interview Explanation

You can explain it in an interview like this:

> **Class:** `LoginPage` is a class that contains the elements and actions related to the login page.
>
> **Object:** `loginPage` is an object/reference of the `LoginPage` class.
>
> **Method:** `enterUsername()`, `enterPassword()`, and `clickLogin()` are methods that perform actions on the login page.
>
> **Constructor:** `LoginPage(WebDriver driver)` initializes the WebDriver object when the LoginPage object is created.

---

# Key Line

```java
LoginPage loginPage = new LoginPage(driver);
```

This means:

1. `LoginPage` → Class
2. `loginPage` → Object/reference variable
3. `new` → Creates an object
4. `LoginPage(driver)` → Calls the constructor
5. `driver` → Passes the WebDriver object to the page object

---

# Summary

| Concept | Selenium Example | Meaning |
|---|---|---|
| Class | `LoginPage` | Blueprint containing page logic |
| Object | `loginPage` | Instance/reference of `LoginPage` |
| Constructor | `LoginPage(driver)` | Initializes the page object |
| Method | `clickLogin()` | Performs an action |
| WebDriver Object | `driver` | Represents browser session |
| Selenium Method | `driver.get()` | Opens a URL |
| Selenium Method | `driver.getTitle()` | Gets page title |
| Selenium Method | `driver.quit()` | Closes browser/session |

## Simple Formula

```text
Class  → Blueprint
Object → Instance of Class
Method → Action performed by Object
```

### Selenium Example

```text
LoginPage
    ↓
  Class
    ↓
loginPage
    ↓
 Object
    ↓
clickLogin()
    ↓
 Method
```


---

# Java Notes for Selenium Automation

## 1. Java Basics

Java is an **object-oriented, class-based programming language** commonly used for Selenium automation.

Important Java concepts for automation:

- Variables
- Data Types
- Operators
- Conditional Statements
- Loops
- Methods
- Classes and Objects
- Constructors
- Inheritance
- Polymorphism
- Encapsulation
- Abstraction
- Interfaces
- Exception Handling
- Collections
- Strings
- Access Modifiers
- `static` and `final`
- Packages
- Java 8 features such as Lambda Expressions and Streams

---

## 2. Variables

A variable stores data.

```java
String name = "Siva";
int age = 30;
double salary = 60000.50;
boolean isActive = true;
```

### Common Data Types

| Data Type | Example |
|---|---|
| `int` | `int age = 30;` |
| `double` | `double price = 99.99;` |
| `float` | `float value = 10.5f;` |
| `char` | `char grade = 'A';` |
| `boolean` | `boolean status = true;` |
| `String` | `String name = "Siva";` |

---

## 3. Conditional Statements

### if

```java
if (age >= 18) {
    System.out.println("Adult");
}
```

### if-else

```java
if (age >= 18) {
    System.out.println("Adult");
} else {
    System.out.println("Minor");
}
```

### else-if

```java
if (marks >= 90) {
    System.out.println("A Grade");
} else if (marks >= 75) {
    System.out.println("B Grade");
} else {
    System.out.println("C Grade");
}
```

### switch

```java
switch (browser) {
    case "chrome":
        System.out.println("Chrome browser");
        break;

    case "firefox":
        System.out.println("Firefox browser");
        break;

    default:
        System.out.println("Invalid browser");
}
```

---

## 4. Loops

### for loop

```java
for (int i = 1; i <= 5; i++) {
    System.out.println(i);
}
```

### while loop

```java
int i = 1;

while (i <= 5) {
    System.out.println(i);
    i++;
}
```

### do-while loop

```java
int i = 1;

do {
    System.out.println(i);
    i++;
} while (i <= 5);
```

### Enhanced for loop

```java
String[] browsers = {"Chrome", "Firefox", "Edge"};

for (String browser : browsers) {
    System.out.println(browser);
}
```

---

## 5. Methods

A method is a reusable block of code.

```java
public void login() {
    System.out.println("User logged in");
}
```

### Method with parameters

```java
public void login(String username, String password) {
    System.out.println(username);
}
```

### Method with return value

```java
public int add(int a, int b) {
    return a + b;
}
```

Usage:

```java
int result = add(10, 20);
```

---

## 6. Constructor

A constructor is used to initialize an object.

```java
public class LoginPage {

    WebDriver driver;

    public LoginPage(WebDriver driver) {
        this.driver = driver;
    }
}
```

Important points:

- Constructor name must match the class name.
- Constructor does not have a return type.
- Constructor is called when an object is created.
- Constructors are heavily used in Selenium Page Object Model.

Example:

```java
LoginPage loginPage = new LoginPage(driver);
```

---

## 7. `this` Keyword

`this` refers to the current object.

```java
public class LoginPage {

    WebDriver driver;

    public LoginPage(WebDriver driver) {
        this.driver = driver;
    }
}
```

Here:

```java
this.driver
```

refers to the instance variable, while:

```java
driver
```

refers to the constructor parameter.

---

# 8. Four Pillars of OOP

## Encapsulation

Wrapping data and methods together inside a class and controlling access using access modifiers.

```java
public class Employee {

    private String name;

    public void setName(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }
}
```

In Selenium, Page Object Model commonly uses encapsulation to keep page elements and page actions organized.

---

## Inheritance

One class can acquire properties and methods from another class.

```java
class BaseTest {

    public void launchBrowser() {
        System.out.println("Browser launched");
    }
}

class LoginTest extends BaseTest {

    public void testLogin() {
        launchBrowser();
    }
}
```

In Selenium frameworks, a `BaseTest` class is commonly extended by test classes.

---

## Polymorphism

Polymorphism means **one name, multiple forms**.

### Method Overloading

Same method name with different parameters.

```java
public void login(String username) {
}

public void login(String username, String password) {
}
```

### Method Overriding

A child class provides its own implementation of a parent method.

```java
class BasePage {

    public void open() {
        System.out.println("Opening page");
    }
}

class LoginPage extends BasePage {

    @Override
    public void open() {
        System.out.println("Opening login page");
    }
}
```

---

## Abstraction

Showing essential functionality while hiding implementation details.

### Abstract class

```java
abstract class BasePage {

    abstract void loadPage();

    void closeBrowser() {
        System.out.println("Browser closed");
    }
}
```

### Interface

```java
interface LoginActions {

    void login();
}
```

A class implements an interface:

```java
class LoginPage implements LoginActions {

    @Override
    public void login() {
        System.out.println("Login");
    }
}
```

Selenium itself makes extensive use of interfaces. For example:

```java
WebDriver driver = new ChromeDriver();
```

`WebDriver` is an interface, while `ChromeDriver` is a concrete implementation.

---

# 9. Access Modifiers

| Modifier | Access |
|---|---|
| `public` | Accessible from anywhere |
| `protected` | Same package + subclasses |
| Default | Same package |
| `private` | Same class only |

Example:

```java
public class Employee {

    private String name;

    public void setName(String name) {
        this.name = name;
    }
}
```

---

# 10. String

`String` is used to store text.

```java
String browser = "Chrome";
String username = "Siva";
```

Common methods:

```java
browser.length();
browser.toUpperCase();
browser.toLowerCase();
browser.contains("Chrome");
browser.equals("Chrome");
browser.trim();
browser.substring(0, 3);
```

Example:

```java
String actualTitle = driver.getTitle();

if (actualTitle.equals("Google")) {
    System.out.println("Title verified");
}
```

---

# 11. Arrays

An array stores multiple values of the same type.

```java
String[] browsers = {"Chrome", "Firefox", "Edge"};
```

Accessing values:

```java
System.out.println(browsers[0]);
```

Output:

```text
Chrome
```

Looping:

```java
for (String browser : browsers) {
    System.out.println(browser);
}
```

---

# 12. Collections

Java Collections are extremely important in Selenium automation.

## List

Allows duplicate values and maintains insertion order.

```java
List<String> browsers = new ArrayList<>();

browsers.add("Chrome");
browsers.add("Firefox");
browsers.add("Chrome");
```

## Set

Does not allow duplicate values.

```java
Set<String> browsers = new HashSet<>();

browsers.add("Chrome");
browsers.add("Firefox");
browsers.add("Chrome");
```

## Map

Stores data as key-value pairs.

```java
Map<String, String> users = new HashMap<>();

users.put("username", "Siva");
users.put("password", "Password123");
```

### Selenium Example

You may use collections when working with multiple web elements:

```java
List<WebElement> links = driver.findElements(By.tagName("a"));

for (WebElement link : links) {
    System.out.println(link.getText());
}
```

---

# 13. Exception Handling

Exception handling prevents unexpected errors from terminating the program without proper handling.

```java
try {
    driver.findElement(By.id("username")).click();
} catch (Exception e) {
    System.out.println("Element could not be clicked");
}
```

### finally

```java
try {
    System.out.println("Test execution");
} catch (Exception e) {
    System.out.println("Exception occurred");
} finally {
    driver.quit();
}
```

Common Selenium-related exceptions:

- `NoSuchElementException`
- `TimeoutException`
- `StaleElementReferenceException`
- `ElementNotInteractableException`
- `ElementClickInterceptedException`
- `WebDriverException`

---

# 14. Static Keyword

`static` belongs to the class rather than a specific object.

```java
public class TestData {

    static String browser = "Chrome";
}
```

Access it without creating an object:

```java
System.out.println(TestData.browser);
```

---

# 15. Final Keyword

`final` prevents a variable, method, or class from being changed or overridden.

```java
final String BROWSER = "Chrome";
```

The value cannot be reassigned.

---

# 16. Java OOP Example in Selenium

```java
public class LoginPage {

    private WebDriver driver;

    public LoginPage(WebDriver driver) {
        this.driver = driver;
    }

    public void enterUsername(String username) {
        driver.findElement(By.id("username")).sendKeys(username);
    }

    public void enterPassword(String password) {
        driver.findElement(By.id("password")).sendKeys(password);
    }

    public void clickLogin() {
        driver.findElement(By.id("login")).click();
    }
}
```

This example demonstrates:

- **Class** → `LoginPage`
- **Object** → `loginPage`
- **Constructor** → `LoginPage(WebDriver driver)`
- **Encapsulation** → `private WebDriver driver`
- **Methods** → `enterUsername()`, `enterPassword()`, `clickLogin()`
- **Object creation** → `new LoginPage(driver)`

---

# 17. Important Java Topics for Selenium Interviews

Prioritize these topics:

1. Classes and Objects
2. Methods
3. Constructors
4. `this` keyword
5. `static` keyword
6. `final` keyword
7. Method Overloading
8. Method Overriding
9. Inheritance
10. Encapsulation
11. Abstraction
12. Interfaces
13. Strings
14. Arrays
15. Collections
16. Exception Handling
17. Access Modifiers
18. `==` vs `.equals()`
19. `String` vs `StringBuilder` vs `StringBuffer`
20. `ArrayList` vs `LinkedList`
21. `HashMap` vs `HashSet`
22. `HashMap` vs `TreeMap`
23. Checked vs Unchecked Exceptions
24. `throw` vs `throws`
25. Java 8 Lambda Expressions
26. Streams
27. Wrapper Classes
28. `final`, `finally`, and `finalize`
29. Heap and Stack basics
30. Garbage Collection basics

---

# Quick Revision

```text
Class       → Blueprint
Object      → Instance of a class
Method      → Action/behavior
Constructor → Initializes an object
Inheritance → Reuse parent class functionality
Polymorphism→ One interface/name, multiple forms
Encapsulation → Data hiding + controlled access
Abstraction → Hide implementation details
Interface   → Defines a contract
Collection  → Stores groups of objects
Exception   → Handles runtime problems
```

## Selenium Connection

```text
Java
 │
 ├── Class
 │     └── LoginPage
 │
 ├── Object
 │     └── loginPage
 │
 ├── Constructor
 │     └── LoginPage(driver)
 │
 ├── Methods
 │     ├── enterUsername()
 │     ├── enterPassword()
 │     └── clickLogin()
 │
 ├── Inheritance
 │     └── BaseTest → LoginTest
 │
 ├── Encapsulation
 │     └── private WebDriver
 │
 ├── Interface
 │     └── WebDriver
 │
 └── Collection
       └── List<WebElement>
```
