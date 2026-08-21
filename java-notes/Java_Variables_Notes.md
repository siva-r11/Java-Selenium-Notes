# Variables in Java

## 1. What is a Variable?

A **variable** is a named storage location used to store a value or a reference to an object during program execution.

### Basic Syntax

```java
dataType variableName = value;
```

Example:

```java
int age = 30;
String name = "Siva";
boolean isActive = true;
```

---

# 2. Types of Variables in Java

Java variables are mainly divided into three types:

1. Local Variable
2. Instance Variable
3. Static/Class Variable

---

# 3. Local Variable

A variable declared inside a **method, constructor, or block** is called a local variable.

```java
public void login() {

    String username = "Siva";
    int attempts = 3;

    System.out.println(username);
}
```

Here:

```text
username → Local variable
attempts → Local variable
```

### Characteristics

- Declared inside a method, constructor, or block.
- Scope is limited to that method or block.
- Local variables do not receive default values.
- They must be initialized before use.

Example:

```java
public void test() {

    int age;

    System.out.println(age); // Compilation error
}
```

Correct:

```java
int age = 30;
System.out.println(age);
```

---

# 4. Instance Variable

A variable declared **inside a class but outside methods, constructors, and blocks** is called an instance variable.

```java
class Employee {

    String name;
    int age;

    void display() {
        System.out.println(name);
        System.out.println(age);
    }
}
```

Here:

```text
name → Instance variable
age  → Instance variable
```

Each object gets its own copy of instance variables.

```java
Employee emp1 = new Employee();
Employee emp2 = new Employee();

emp1.name = "Siva";
emp2.name = "John";
```

Result:

```text
emp1.name → Siva
emp2.name → John
```

---

# 5. Static Variable

A variable declared using the `static` keyword is called a **static variable** or **class variable**.

```java
class Employee {

    String name;

    static String company = "ABC Technologies";
}
```

A static variable belongs to the **class**, not to individual objects.

It can be accessed using the class name:

```java
System.out.println(Employee.company);
```

Example:

```java
class Employee {

    String name;
    static String company = "ABC Technologies";
}
```

```java
Employee emp1 = new Employee();
Employee emp2 = new Employee();

emp1.name = "Siva";
emp2.name = "John";

System.out.println(Employee.company);
```

Both objects share the same `company` variable.

---

# 6. Local vs Instance vs Static Variables

| Type | Declared Where? | Belongs To | Default Value |
|---|---|---|---|
| Local | Inside method/block/constructor | Method/block | No |
| Instance | Inside class, outside methods | Object | Yes |
| Static | Inside class with `static` | Class | Yes |

---

# 7. Primitive Data Types

Java has eight primitive data types.

| Data Type | Example | Typical Size |
|---|---|---:|
| `byte` | `byte age = 30;` | 8-bit |
| `short` | `short value = 1000;` | 16-bit |
| `int` | `int age = 30;` | 32-bit |
| `long` | `long salary = 60000L;` | 64-bit |
| `float` | `float price = 10.5f;` | 32-bit |
| `double` | `double price = 99.99;` | 64-bit |
| `char` | `char grade = 'A';` | 16-bit |
| `boolean` | `boolean status = true;` | JVM-specific |

Example:

```java
byte age = 30;
short number = 1000;
int salary = 60000;
long population = 8000000000L;

float price = 10.5f;
double percentage = 95.75;

char grade = 'A';
boolean passed = true;
```

---

# 8. Reference Variables

A reference variable stores a **reference to an object**.

Example:

```java
String name = "Siva";
```

`name` is a reference variable referring to a `String` object.

### Selenium Example

```java
WebDriver driver = new ChromeDriver();
```

Here:

```text
WebDriver              → Reference type
driver                 → Reference variable
new ChromeDriver()     → Object creation
```

Another example:

```java
LoginPage loginPage = new LoginPage(driver);
```

Here:

```text
loginPage                 → Reference variable
LoginPage                 → Class
new LoginPage(driver)     → Creates object
```

---

# 9. Variable Declaration and Initialization

## Declaration

```java
int age;
```

The variable is declared but not initialized.

## Initialization

```java
age = 30;
```

A value is assigned to the variable.

## Declaration + Initialization

```java
int age = 30;
```

This is commonly used in Java programs.

---

# 10. Multiple Variables

You can declare several variables of the same type.

```java
int a = 10;
int b = 20;
int c = 30;
```

Or:

```java
int a = 10, b = 20, c = 30;
```

For readability, separate declarations are generally easier to maintain.

---

# 11. Variable Naming Rules

### Valid Variable Names

```java
int age;
String userName;
int employee123;
double totalAmount;
```

### Invalid Variable Names

```java
int 123employee;   // Invalid: cannot start with a number
int user-name;     // Invalid: hyphen is not allowed
int class;         // Invalid: class is a Java keyword
```

### Recommended Naming Convention

Use **camelCase**:

```java
String firstName;
String lastName;
int employeeAge;
double totalAmount;
```

Constants commonly use **UPPER_SNAKE_CASE**:

```java
final int MAX_RETRY = 3;
```

---

# 12. `final` Variables

A variable declared using `final` cannot be reassigned.

```java
final int MAX_RETRY = 3;
```

This is invalid:

```java
MAX_RETRY = 5; // Compilation error
```

`final` variables are commonly used for constants.

---

# 13. Variable Scope

**Scope** is the region of the program where a variable can be accessed.

Example:

```java
public void test() {

    int age = 30;

    if (age > 18) {

        String message = "Adult";

        System.out.println(message);
    }

    // System.out.println(message); // Compilation error
}
```

`message` is available only inside the `if` block.

### General Rule

```text
Local variable
    ↓
Limited to its method/block

Instance variable
    ↓
Available through an object

Static variable
    ↓
Available through the class
```

---

# 14. Variable Shadowing

When a local variable or parameter has the same name as an instance variable, the local variable or parameter **shadows** the instance variable.

Example:

```java
class Employee {

    String name;

    Employee(String name) {
        this.name = name;
    }
}
```

Here:

```text
this.name → Instance variable
name      → Constructor parameter
```

The `this` keyword identifies the current object's instance variable.

---

# 15. Primitive vs Reference Variables

| Primitive Variable | Reference Variable |
|---|---|
| Stores a primitive value | Stores a reference to an object |
| Examples: `int`, `char`, `boolean` | Examples: `String`, `WebDriver`, `WebElement` |
| Cannot hold `null` | Can hold `null` |
| `int age = 30;` | `WebDriver driver = new ChromeDriver();` |

---

# 16. Variables in Selenium Automation

Variables are used throughout Selenium automation.

### WebDriver Variable

```java
WebDriver driver = new ChromeDriver();
```

### String Variable

```java
String url = "https://example.com";
driver.get(url);
```

### Integer Variable

```java
int timeout = 10;
```

### Boolean Variable

```java
boolean isDisplayed =
        driver.findElement(By.id("login")).isDisplayed();
```

### WebElement Variable

```java
WebElement username =
        driver.findElement(By.id("username"));

username.sendKeys("Siva");
```

### List Variable

```java
List<WebElement> buttons =
        driver.findElements(By.tagName("button"));
```

---

# 17. Complete Selenium Example

```java
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;

import java.util.List;

public class LoginTest {

    // Instance variable
    WebDriver driver;

    // Static variable
    static String browser = "Chrome";

    public void loginTest() {

        // Local variables
        String username = "Siva";
        String password = "Password123";

        driver = new ChromeDriver();

        driver.get("https://example.com/login");

        WebElement usernameField =
                driver.findElement(By.id("username"));

        WebElement passwordField =
                driver.findElement(By.id("password"));

        usernameField.sendKeys(username);
        passwordField.sendKeys(password);

        List<WebElement> buttons =
                driver.findElements(By.tagName("button"));

        System.out.println(
                "Number of buttons: " + buttons.size()
        );

        driver.quit();
    }
}
```

### Variables in This Example

```text
driver
    → Instance variable

browser
    → Static variable

username
password
    → Local variables

usernameField
passwordField
    → Local reference variables

buttons
    → Local reference variable
```

---

# 18. `null` and Reference Variables

A reference variable can hold `null`.

```java
WebDriver driver = null;
```

This means the reference currently does not refer to an object.

Calling a method on a null reference can cause:

```text
NullPointerException
```

Example:

```java
String name = null;

System.out.println(name.length()); // NullPointerException
```

---

# 19. Type Casting and Variables

Type casting is converting one data type into another compatible type.

## Widening Casting

Automatic conversion from smaller to larger compatible type.

```java
int number = 10;
double value = number;
```

## Narrowing Casting

Manual conversion from larger to smaller type.

```java
double value = 10.5;
int number = (int) value;
```

Result:

```text
number = 10
```

---

# 20. `var` Local Variable Type Inference

Java supports `var` for local variable type inference.

```java
var name = "Siva";
var age = 30;
var driver = new ChromeDriver();
```

The compiler determines the type from the initializer.

Important:

- `var` can be used for local variables.
- It cannot be used for instance variables.
- It cannot be used without an initializer.

Invalid:

```java
var age; // Compilation error
```

---

# 21. Constants

A constant is generally declared using `static final`.

```java
class Config {

    static final int TIMEOUT = 10;
    static final String BROWSER = "Chrome";
}
```

Access:

```java
System.out.println(Config.TIMEOUT);
System.out.println(Config.BROWSER);
```

Common naming convention:

```text
UPPER_SNAKE_CASE
```

---

# 22. Important Interview Questions

1. What is a variable in Java?
2. What are the types of variables in Java?
3. What is a local variable?
4. What is an instance variable?
5. What is a static variable?
6. What is the difference between local, instance, and static variables?
7. What are primitive data types?
8. What are reference variables?
9. What is variable scope?
10. What is variable shadowing?
11. What is the purpose of the `final` keyword?
12. What is the difference between declaration and initialization?
13. What are the default values of instance variables?
14. Do local variables have default values?
15. What is a reference variable in Selenium?
16. What is the difference between `WebDriver driver` and `new ChromeDriver()`?
17. What is the difference between primitive and reference variables?
18. What is `null`?
19. What is type casting?
20. What is `var` in Java?
21. What is a constant?
22. How are variables used in Selenium Page Object Model?

---

# 23. Interview Answer

### Question: What are the types of variables in Java?

**Answer:**

> Java has three main types of variables: **local variables, instance variables, and static variables**. Local variables are declared inside methods, constructors, or blocks and their scope is limited to that area. Instance variables are declared inside a class but outside methods and belong to individual objects. Static variables are declared using the `static` keyword and belong to the class, so they are shared among objects.

---

# 24. Easy Way to Remember

```text
Local
  ↓
Inside method/block
  ↓
Belongs to method/block

Instance
  ↓
Inside class
  ↓
Belongs to object

Static
  ↓
Inside class + static
  ↓
Belongs to class
```

---

# 25. Selenium Key Example

```java
WebDriver driver = new ChromeDriver();
```

Remember:

```text
WebDriver
    ↓
Reference type

driver
    ↓
Reference variable

new ChromeDriver()
    ↓
Creates object
```

---

# Quick Revision

| Topic | Key Point |
|---|---|
| Variable | Stores a value or object reference |
| Local | Declared inside method/block/constructor |
| Instance | Belongs to an object |
| Static | Belongs to the class |
| Primitive | Stores primitive values |
| Reference | Refers to objects |
| `final` | Prevents reassignment |
| `null` | Reference points to no object |
| `var` | Local variable type inference |
| Scope | Area where variable can be accessed |

## One-Line Definition

> **A variable in Java is a named storage location used to hold a value or a reference to an object during program execution.**
