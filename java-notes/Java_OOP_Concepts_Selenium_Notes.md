# OOP Concepts in Java

## Introduction

**OOP (Object-Oriented Programming)** is a programming approach where software is designed using **classes and objects**.

Java has four major pillars of OOP:

1. Encapsulation
2. Inheritance
3. Polymorphism
4. Abstraction

Before learning the four pillars, understand **Class and Object**.

---

# 1. Class

A **class** is a blueprint or template used to create objects.

```java
class Employee {

    String name;
    int age;

    void work() {
        System.out.println("Employee is working");
    }
}
```

Here:

- `Employee` → Class
- `name`, `age` → Variables
- `work()` → Method

---

# 2. Object

An **object** is an instance of a class.

```java
Employee emp = new Employee();

emp.name = "Siva";
emp.age = 30;

emp.work();
```

Here:

```text
Employee       → Class
emp            → Object/reference
new Employee() → Creates the object
```

## Selenium Example

```java
WebDriver driver = new ChromeDriver();
```

Here:

- `WebDriver` → Interface
- `driver` → Reference variable
- `ChromeDriver` → Class
- `new ChromeDriver()` → Creates the object

---

# Four Pillars of OOP

# 3. Encapsulation

**Encapsulation means wrapping data and methods together and controlling access to the data.**

It is commonly achieved using:

- `private` variables
- `public` getter/setter methods

## Example

```java
class Employee {

    private String name;
    private int salary;

    public void setName(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }

    public void setSalary(int salary) {
        this.salary = salary;
    }

    public int getSalary() {
        return salary;
    }
}
```

Usage:

```java
Employee emp = new Employee();

emp.setName("Siva");
emp.setSalary(60000);

System.out.println(emp.getName());
System.out.println(emp.getSalary());
```

## Why Encapsulation?

It prevents direct access to important data.

Instead of:

```java
emp.salary = -5000;
```

you control access through:

```java
emp.setSalary(60000);
```

## Selenium Example

Page Object Model commonly uses encapsulation:

```java
public class LoginPage {

    private WebDriver driver;

    public LoginPage(WebDriver driver) {
        this.driver = driver;
    }

    public void login(String username, String password) {
        driver.findElement(By.id("username")).sendKeys(username);
        driver.findElement(By.id("password")).sendKeys(password);
    }
}
```

The internal `driver` is hidden using `private`, while the test interacts with the page through public methods.

---

# 4. Inheritance

**Inheritance allows one class to acquire properties and methods from another class.**

It is achieved using:

```java
extends
```

## Example

```java
class Animal {

    void eat() {
        System.out.println("Animal is eating");
    }
}

class Dog extends Animal {

    void bark() {
        System.out.println("Dog is barking");
    }
}
```

Usage:

```java
Dog dog = new Dog();

dog.eat();
dog.bark();
```

Output:

```text
Animal is eating
Dog is barking
```

`Dog` inherits the `eat()` method from `Animal`.

## Selenium Framework Example

A common automation framework structure is:

```java
class BaseTest {

    WebDriver driver;

    void launchBrowser() {
        driver = new ChromeDriver();
    }
}

class LoginTest extends BaseTest {

    void testLogin() {
        launchBrowser();
    }
}
```

Here:

```text
BaseTest
   ↑
   |
LoginTest
```

`LoginTest` inherits functionality from `BaseTest`.

---

# 5. Polymorphism

**Polymorphism means "many forms."**

Java supports two major types:

1. Compile-time polymorphism
2. Runtime polymorphism

---

## 5.1 Method Overloading

Method overloading is **compile-time polymorphism**.

It means having the same method name with different parameters.

```java
class Calculator {

    int add(int a, int b) {
        return a + b;
    }

    int add(int a, int b, int c) {
        return a + b + c;
    }

    double add(double a, double b) {
        return a + b;
    }
}
```

Usage:

```java
Calculator calculator = new Calculator();

System.out.println(calculator.add(10, 20));
System.out.println(calculator.add(10, 20, 30));
System.out.println(calculator.add(10.5, 20.5));
```

The method name is the same:

```text
add()
```

but the parameters are different.

---

## 5.2 Method Overriding

Method overriding is **runtime polymorphism**.

A child class provides its own implementation of a parent class method.

```java
class Browser {

    void open() {
        System.out.println("Opening browser");
    }
}

class Chrome extends Browser {

    @Override
    void open() {
        System.out.println("Opening Chrome");
    }
}
```

Usage:

```java
Browser browser = new Chrome();

browser.open();
```

Output:

```text
Opening Chrome
```

Even though the reference type is `Browser`, Java executes the `Chrome` implementation at runtime.

## Selenium Connection

This concept is important because Selenium uses interfaces and implementations:

```java
WebDriver driver = new ChromeDriver();
```

You can also use:

```java
WebDriver driver = new FirefoxDriver();
```

The same `WebDriver` interface can work with different browser implementations.

---

# 6. Abstraction

**Abstraction means hiding implementation details and exposing only the required functionality.**

Java achieves abstraction mainly through:

- Abstract classes
- Interfaces

---

## 6.1 Abstract Class

```java
abstract class Vehicle {

    abstract void start();

    void stop() {
        System.out.println("Vehicle stopped");
    }
}
```

Child class:

```java
class Car extends Vehicle {

    @Override
    void start() {
        System.out.println("Car started");
    }
}
```

Usage:

```java
Car car = new Car();

car.start();
car.stop();
```

Output:

```text
Car started
Vehicle stopped
```

You cannot directly create an object of an abstract class:

```java
Vehicle vehicle = new Vehicle(); // ❌
```

---

# 7. Interface

An interface defines a **contract** that implementing classes must follow.

```java
interface Login {

    void login();
}
```

Implementation:

```java
class AdminLogin implements Login {

    @Override
    public void login() {
        System.out.println("Admin logged in");
    }
}
```

Usage:

```java
Login login = new AdminLogin();

login.login();
```

## Selenium Example

One of the most important examples:

```java
WebDriver driver = new ChromeDriver();
```

`WebDriver` is an interface.

`ChromeDriver` is a class that implements the WebDriver contract.

This allows Selenium to support multiple browsers:

```java
WebDriver driver = new ChromeDriver();
```

or:

```java
WebDriver driver = new FirefoxDriver();
```

---

# 8. Class vs Object vs OOP Pillars

| Concept | Meaning | Java Example |
|---|---|---|
| Class | Blueprint | `LoginPage` |
| Object | Instance of class | `loginPage` |
| Encapsulation | Data hiding/control | `private WebDriver driver` |
| Inheritance | Reuse parent functionality | `LoginTest extends BaseTest` |
| Polymorphism | Many forms | `WebDriver driver = new ChromeDriver()` |
| Abstraction | Hide implementation | `WebDriver` interface |

---

# 9. Real Selenium Framework Example

A typical Selenium framework can combine all four OOP concepts.

## BaseTest

```java
public class BaseTest {

    protected WebDriver driver;

    public void launchBrowser() {
        driver = new ChromeDriver();
    }
}
```

## LoginPage

```java
public class LoginPage {

    private WebDriver driver;

    public LoginPage(WebDriver driver) {
        this.driver = driver;
    }

    public void login(String username, String password) {
        driver.findElement(By.id("username")).sendKeys(username);
        driver.findElement(By.id("password")).sendKeys(password);
    }
}
```

## LoginTest

```java
public class LoginTest extends BaseTest {

    public void testLogin() {

        launchBrowser();

        LoginPage loginPage = new LoginPage(driver);

        loginPage.login("siva", "password123");

        driver.quit();
    }
}
```

## OOP Concepts Used

```text
                    OOP
                     |
        ┌────────────┼────────────┐
        ↓            ↓            ↓
  Encapsulation  Inheritance  Polymorphism
        |            |            |
 private driver  extends      WebDriver
 public methods  BaseTest     = ChromeDriver
        |
        └───────────────┐
                        ↓
                   Abstraction
                        |
                  WebDriver API
```

---

# 10. Interview Answer

If an interviewer asks:

**"What are the OOP concepts in Java?"**

You can answer:

> Java has four major OOP concepts: **Encapsulation, Inheritance, Polymorphism, and Abstraction**.
>
> **Encapsulation** is used to hide data and provide controlled access through methods.
>
> **Inheritance** allows a child class to reuse properties and methods of a parent class using `extends`.
>
> **Polymorphism** means one interface or method can have multiple forms. It includes method overloading and method overriding.
>
> **Abstraction** means hiding implementation details and exposing only the required functionality. Java achieves this using abstract classes and interfaces.
>
> In Selenium frameworks, these concepts are commonly used in **Page Object Model, Base Test classes, WebDriver interfaces, and reusable automation components**.

---

# 11. Easy Way to Remember

## E-I-P-A

```text
E → Encapsulation
I → Inheritance
P → Polymorphism
A → Abstraction
```

### Simple Definitions

```text
Encapsulation → Data hiding
Inheritance   → Code reusability
Polymorphism  → Many forms
Abstraction   → Hide implementation details
```

---

# 12. OOP + Selenium Quick Revision

```text
Class
  ↓
LoginPage

Object
  ↓
loginPage

Encapsulation
  ↓
private WebDriver driver

Inheritance
  ↓
LoginTest extends BaseTest

Polymorphism
  ↓
WebDriver driver = new ChromeDriver()

Abstraction
  ↓
WebDriver interface
```

---

# 13. Important Interview Questions

1. What is OOP?
2. What are the four pillars of OOP?
3. What is a class?
4. What is an object?
5. What is encapsulation?
6. Why do we use encapsulation?
7. What is inheritance?
8. What are the types of inheritance supported by Java?
9. What is polymorphism?
10. What is method overloading?
11. What is method overriding?
12. Difference between overloading and overriding?
13. What is abstraction?
14. Difference between abstract class and interface?
15. What is an interface?
16. Can we create an object of an abstract class?
17. How does Selenium use OOP concepts?
18. Why is `WebDriver` an interface?
19. Why do we use `WebDriver driver = new ChromeDriver()`?
20. How is inheritance used in a Selenium framework?
21. How is encapsulation used in Page Object Model?
22. How is polymorphism used in Selenium?
23. What is the difference between `extends` and `implements`?
24. What is the difference between class and object?
25. What is the difference between abstraction and encapsulation?
