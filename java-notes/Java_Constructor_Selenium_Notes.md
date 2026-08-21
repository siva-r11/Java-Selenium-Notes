# Constructor in Java

## 1. What is a Constructor?

A **constructor** is a special block in Java that is used to **initialize an object**.

A constructor is automatically called when an object is created using the `new` keyword.

```java
class Employee {

    String name;
    int age;

    // Constructor
    Employee() {
        name = "Siva";
        age = 30;
    }

    void display() {
        System.out.println(name);
        System.out.println(age);
    }
}
```

Creating the object:

```java
Employee emp = new Employee();

emp.display();
```

When this line executes:

```java
Employee emp = new Employee();
```

Java automatically calls:

```java
Employee()
```

---

# 2. Rules of a Constructor

## Rule 1: Constructor name must be the same as the class name

```java
class Employee {

    Employee() {
    }
}
```

```text
Class name  → Employee
Constructor → Employee()
```

---

## Rule 2: Constructor cannot have a return type

Correct:

```java
Employee() {
}
```

Incorrect:

```java
void Employee() {
}
```

The second example is a **method**, not a constructor.

---

## Rule 3: Constructor is called automatically

```java
Employee emp = new Employee();
```

`new Employee()` automatically calls the constructor.

---

## Rule 4: Constructor is mainly used for initialization

```java
class Employee {

    String name;

    Employee() {
        name = "Siva";
    }
}
```

---

# 3. Types of Constructors

The commonly discussed types are:

1. No-Argument Constructor
2. Parameterized Constructor

---

# 4. No-Argument Constructor

A constructor without parameters is called a **no-argument constructor**.

```java
class Employee {

    String name;

    Employee() {
        name = "Siva";
    }
}
```

Create an object:

```java
Employee emp = new Employee();

System.out.println(emp.name);
```

Output:

```text
Siva
```

---

# 5. Parameterized Constructor

A constructor that accepts parameters is called a **parameterized constructor**.

```java
class Employee {

    String name;
    int age;

    Employee(String name, int age) {
        this.name = name;
        this.age = age;
    }
}
```

Create an object:

```java
Employee emp = new Employee("Siva", 30);

System.out.println(emp.name);
System.out.println(emp.age);
```

Output:

```text
Siva
30
```

---

# 6. `this` Keyword in Constructor

Consider:

```java
class Employee {

    String name;

    Employee(String name) {
        this.name = name;
    }
}
```

There are two `name` variables:

```text
this.name → Instance variable
name      → Constructor parameter
```

Therefore:

```java
this.name = name;
```

means:

> Assign the constructor parameter `name` to the object's instance variable `name`.

---

# 7. Constructor Overloading

Java supports **constructor overloading**.

Constructor overloading means having multiple constructors with different parameter lists.

```java
class Employee {

    String name;
    int age;

    // Constructor 1
    Employee() {
        name = "Unknown";
        age = 0;
    }

    // Constructor 2
    Employee(String name) {
        this.name = name;
    }

    // Constructor 3
    Employee(String name, int age) {
        this.name = name;
        this.age = age;
    }
}
```

Objects can be created in different ways:

```java
Employee emp1 = new Employee();

Employee emp2 = new Employee("Siva");

Employee emp3 = new Employee("Siva", 30);
```

Constructor overloading is an example of **compile-time polymorphism**.

---

# 8. Constructor vs Method

| Constructor | Method |
|---|---|
| Initializes an object | Performs an operation |
| Same name as class | Can have any valid name |
| No return type | Can have a return type |
| Called automatically when object is created | Usually called explicitly |
| Cannot be inherited | Methods can be inherited |
| Mainly used for initialization | Mainly used for behavior/functionality |

Example:

```java
class Employee {

    // Constructor
    Employee() {
        System.out.println("Object created");
    }

    // Method
    void work() {
        System.out.println("Employee is working");
    }
}
```

Usage:

```java
Employee emp = new Employee();  // Constructor called

emp.work();                     // Method called
```

Output:

```text
Object created
Employee is working
```

---

# 9. Constructor in Selenium

Constructors are **very important in Selenium Page Object Model (POM)**.

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

## LoginTest.java

```java
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;

public class LoginTest {

    public static void main(String[] args) {

        WebDriver driver = new ChromeDriver();

        driver.get("https://example.com/login");

        LoginPage loginPage = new LoginPage(driver);

        loginPage.enterUsername("siva");
        loginPage.enterPassword("password123");
        loginPage.clickLogin();

        driver.quit();
    }
}
```

The important line is:

```java
LoginPage loginPage = new LoginPage(driver);
```

Here:

```text
LoginPage
    ↓
Class

loginPage
    ↓
Object/reference

new LoginPage(driver)
    ↓
Creates object + calls constructor
```

The constructor:

```java
public LoginPage(WebDriver driver) {
    this.driver = driver;
}
```

passes the Selenium `WebDriver` instance from the test class into the `LoginPage`.

This allows the page class to use:

```java
driver.findElement(...)
```

---

# 10. Constructor Chaining

One constructor can call another constructor in the same class using:

```java
this()
```

Example:

```java
class Employee {

    String name;
    int age;

    Employee() {
        this("Unknown", 0);
    }

    Employee(String name, int age) {
        this.name = name;
        this.age = age;
    }
}
```

Here:

```java
this("Unknown", 0);
```

calls another constructor in the same class.

---

# 11. Calling Parent Constructor

A child class can call the parent constructor using:

```java
super();
```

Example:

```java
class Employee {

    Employee() {
        System.out.println("Employee constructor");
    }
}

class Developer extends Employee {

    Developer() {
        super();
        System.out.println("Developer constructor");
    }
}
```

Usage:

```java
Developer developer = new Developer();
```

Output:

```text
Employee constructor
Developer constructor
```

The parent constructor executes before the child constructor.

---

# 12. What Happens If You Don't Create a Constructor?

If you don't define **any constructor**, Java provides a default no-argument constructor automatically.

Example:

```java
class Employee {

    String name;
}
```

Java effectively provides:

```java
Employee() {
}
```

However, if you define your own constructor:

```java
class Employee {

    Employee(String name) {
        this.name = name;
    }
}
```

Java does **not** automatically provide a no-argument constructor.

Therefore:

```java
Employee emp = new Employee(); // ❌ Compilation error
```

You need to use:

```java
Employee emp = new Employee("Siva");
```

Or explicitly define a no-argument constructor:

```java
class Employee {

    Employee() {
    }

    Employee(String name) {
        this.name = name;
    }
}
```

---

# 13. Constructor and Object Creation

Consider:

```java
Employee emp = new Employee("Siva", 30);
```

Breakdown:

```text
Employee
   ↓
Reference type / Class

emp
   ↓
Reference variable

new
   ↓
Creates an object

Employee("Siva", 30)
   ↓
Calls parameterized constructor
```

---

# 14. Constructor Execution Flow

Example:

```java
class Employee {

    Employee() {
        System.out.println("Constructor executed");
    }
}

public class Test {

    public static void main(String[] args) {

        System.out.println("Before object");

        Employee emp = new Employee();

        System.out.println("After object");
    }
}
```

Output:

```text
Before object
Constructor executed
After object
```

The constructor executes during object creation.

---

# 15. Important Constructor Interview Questions

1. What is a constructor in Java?
2. Why do we use constructors?
3. What are the rules of a constructor?
4. What is a no-argument constructor?
5. What is a parameterized constructor?
6. What is constructor overloading?
7. Can constructors be overloaded?
8. Can a constructor have a return type?
9. Can a constructor be `static`?
10. Can a constructor be `final`?
11. Can a constructor be `private`?
12. What happens if no constructor is defined?
13. What is the difference between a constructor and a method?
14. What is constructor chaining?
15. What is `this()`?
16. What is `super()`?
17. When is the parent constructor called?
18. How are constructors used in Selenium Page Object Model?
19. Why do we pass `WebDriver` through a page class constructor?
20. What happens when `new` is used?

---

# 16. Interview Answer

If the interviewer asks:

**"What is a constructor in Java?"**

You can answer:

> A constructor is a special member of a class used to initialize objects. It has the same name as the class and does not have a return type. It is automatically invoked when an object is created using the `new` keyword. Constructors can be no-argument or parameterized, and Java supports constructor overloading. In Selenium Page Object Model, constructors are commonly used to initialize and pass the WebDriver instance to page classes.

---

# 17. Easy Way to Remember

```text
Constructor
     ↓
Same name as Class
     ↓
No return type
     ↓
Called automatically
     ↓
Initializes Object
```

## Selenium Example

```java
LoginPage loginPage = new LoginPage(driver);
```

```text
LoginPage(driver)
       ↓
   Constructor
```

---

# Quick Revision

| Topic | Key Point |
|---|---|
| Constructor | Initializes an object |
| Name | Same as class |
| Return type | None |
| Invocation | Automatically during object creation |
| Keyword used for object creation | `new` |
| No-argument constructor | Has no parameters |
| Parameterized constructor | Accepts parameters |
| Constructor overloading | Multiple constructors with different parameters |
| `this()` | Calls another constructor in the same class |
| `super()` | Calls parent constructor |
| Selenium/POM | Used to initialize `WebDriver` |

## One-Line Definition

> **A constructor is a special class member that is automatically called during object creation and is primarily used to initialize the object.**
