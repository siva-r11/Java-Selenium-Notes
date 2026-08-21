# Conditional Statements in Java

Conditional statements are used to make decisions in a Java program. They execute different blocks of code depending on whether a condition is `true` or `false`.

## Types of Conditional Statements

1. `if`
2. `if-else`
3. `if-else-if`
4. Nested `if`
5. `switch`

---

## 1. `if` Statement

Executes a block of code only when the condition is `true`.

```java
int age = 20;

if (age >= 18) {
    System.out.println("Eligible to vote");
}
```

**Output:**
```text
Eligible to vote
```

---

## 2. `if-else` Statement

Executes one block when the condition is `true` and another when it is `false`.

```java
int age = 16;

if (age >= 18) {
    System.out.println("Eligible to vote");
} else {
    System.out.println("Not eligible to vote");
}
```

**Output:**
```text
Not eligible to vote
```

---

## 3. `if-else-if` Statement

Used when there are multiple conditions.

```java
int marks = 75;

if (marks >= 90) {
    System.out.println("Grade A+");
} else if (marks >= 75) {
    System.out.println("Grade A");
} else if (marks >= 60) {
    System.out.println("Grade B");
} else if (marks >= 50) {
    System.out.println("Grade C");
} else {
    System.out.println("Fail");
}
```

**Output:**
```text
Grade A
```

---

## 4. Nested `if`

An `if` statement inside another `if` statement.

```java
int age = 25;
boolean hasLicense = true;

if (age >= 18) {
    if (hasLicense) {
        System.out.println("Can drive");
    } else {
        System.out.println("License required");
    }
} else {
    System.out.println("Not eligible to drive");
}
```

**Output:**
```text
Can drive
```

---

## 5. `switch` Statement

Used when you need to compare a variable against multiple fixed values.

```java
int day = 2;

switch (day) {
    case 1:
        System.out.println("Monday");
        break;

    case 2:
        System.out.println("Tuesday");
        break;

    case 3:
        System.out.println("Wednesday");
        break;

    default:
        System.out.println("Invalid day");
}
```

**Output:**
```text
Tuesday
```

---

# Selenium Examples

Conditional statements are frequently used in Selenium automation.

## Example 1: Check Whether an Element Is Displayed

```java
if (driver.findElement(By.id("loginButton")).isDisplayed()) {
    driver.findElement(By.id("loginButton")).click();
} else {
    System.out.println("Login button is not displayed");
}
```

## Example 2: Validate Page Title

```java
String title = driver.getTitle();

if (title.equals("Amazon")) {
    System.out.println("Correct page opened");
} else {
    System.out.println("Incorrect page");
}
```

---

# Conditional Operators in Java

| Operator | Meaning | Example |
|---|---|---|
| `==` | Equal to | `a == b` |
| `!=` | Not equal to | `a != b` |
| `>` | Greater than | `a > b` |
| `<` | Less than | `a < b` |
| `>=` | Greater than or equal to | `a >= b` |
| `<=` | Less than or equal to | `a <= b` |
| `&&` | Logical AND | `a > 10 && b > 10` |
| `||` | Logical OR | `a > 10 || b > 10` |
| `!` | Logical NOT | `!isValid` |

---

# Quick Comparison

| Statement | Use |
|---|---|
| `if` | One condition |
| `if-else` | Two possible outcomes |
| `if-else-if` | Multiple conditions |
| Nested `if` | Condition inside another condition |
| `switch` | Multiple fixed values |

---

# Interview Notes

- `if` executes code only when its condition evaluates to `true`.
- `if-else` provides two possible execution paths.
- `if-else-if` is useful for checking multiple conditions.
- Nested `if` means placing one conditional statement inside another.
- `switch` is useful for selecting one execution path from multiple fixed values.
- Java conditions return a boolean result: `true` or `false`.
- In Selenium automation, conditional statements are commonly used for element visibility, page validation, status checks, and test-flow decisions.
