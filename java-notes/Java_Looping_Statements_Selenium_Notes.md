# Looping Statements in Java

## Introduction

Looping statements are used to **execute a block of code repeatedly** until a specific condition is met.

Java has three main loops:

1. `for` loop
2. `while` loop
3. `do-while` loop

Java also provides the **enhanced `for` loop (for-each)**, which is commonly used with arrays and collections.

---

# 1. `for` Loop

Use a `for` loop when you know how many times you want to execute the code.

## Syntax

```java
for (initialization; condition; increment/decrement) {
    // code
}
```

## Example

```java
for (int i = 1; i <= 5; i++) {
    System.out.println(i);
}
```

Output:

```text
1
2
3
4
5
```

## Execution Flow

```text
int i = 1
    ↓
i <= 5 ?
    ↓
Execute code
    ↓
i++
    ↓
Check condition again
```

---

# 2. `while` Loop

A `while` loop executes the code **as long as the condition is true**.

## Syntax

```java
while (condition) {
    // code
}
```

## Example

```java
int i = 1;

while (i <= 5) {
    System.out.println(i);
    i++;
}
```

Output:

```text
1
2
3
4
5
```

## Important

The condition is checked **before** executing the loop body.

Therefore, if the condition is initially false, the loop will not execute even once.

```java
int i = 10;

while (i <= 5) {
    System.out.println(i);
}
```

No output.

---

# 3. `do-while` Loop

A `do-while` loop executes the code **at least once**, because the condition is checked after the loop body.

## Syntax

```java
do {
    // code
} while (condition);
```

## Example

```java
int i = 1;

do {
    System.out.println(i);
    i++;
} while (i <= 5);
```

Output:

```text
1
2
3
4
5
```

Even when the condition is initially false:

```java
int i = 10;

do {
    System.out.println(i);
} while (i <= 5);
```

Output:

```text
10
```

The body executes before the condition is checked.

---

# 4. Enhanced `for` Loop / For-Each

The enhanced `for` loop is useful for iterating through **arrays and collections**.

## Array Example

```java
String[] browsers = {
    "Chrome",
    "Firefox",
    "Edge"
};

for (String browser : browsers) {
    System.out.println(browser);
}
```

Output:

```text
Chrome
Firefox
Edge
```

## Syntax

```java
for (dataType variable : collectionOrArray) {
    // code
}
```

---

# 5. `break` Statement

`break` is used to **terminate a loop immediately**.

```java
for (int i = 1; i <= 10; i++) {

    if (i == 5) {
        break;
    }

    System.out.println(i);
}
```

Output:

```text
1
2
3
4
```

When `i` becomes `5`, `break` terminates the loop.

---

# 6. `continue` Statement

`continue` skips the current iteration and moves to the next iteration.

```java
for (int i = 1; i <= 5; i++) {

    if (i == 3) {
        continue;
    }

    System.out.println(i);
}
```

Output:

```text
1
2
4
5
```

The value `3` is skipped.

---

# 7. Nested Loop

A loop inside another loop is called a **nested loop**.

```java
for (int i = 1; i <= 3; i++) {

    for (int j = 1; j <= 3; j++) {
        System.out.println(i + " " + j);
    }
}
```

Output:

```text
1 1
1 2
1 3
2 1
2 2
2 3
3 1
3 2
3 3
```

---

# 8. Selenium Example — Loop Through Web Elements

This is very common in Selenium automation.

```java
List<WebElement> links =
        driver.findElements(By.tagName("a"));

for (WebElement link : links) {
    System.out.println(link.getText());
}
```

Here:

```java
driver.findElements(By.tagName("a"))
```

returns a `List<WebElement>`.

The enhanced `for` loop iterates through every link.

---

# 9. Selenium Example — Find and Click a Button

Suppose a page contains multiple buttons and you want to click the button named `Login`.

```java
List<WebElement> buttons =
        driver.findElements(By.tagName("button"));

for (WebElement button : buttons) {

    if (button.getText().equals("Login")) {
        button.click();
        break;
    }
}
```

Here:

- `for` → loops through buttons
- `if` → checks the button text
- `click()` → clicks the matching button
- `break` → stops searching after finding the button

---

# 10. Selenium Example — Verify Multiple Links

```java
List<WebElement> links =
        driver.findElements(By.tagName("a"));

for (WebElement link : links) {

    String text = link.getText();

    if (!text.isEmpty()) {
        System.out.println("Link: " + text);
    }
}
```

This can be useful when validating multiple elements on a webpage.

---

# 11. Difference Between Loops

| Loop | Condition Checked | Minimum Execution | Best Used For |
|---|---|---:|---|
| `for` | Before | 0 | Known number of iterations |
| `while` | Before | 0 | Unknown number of iterations |
| `do-while` | After | 1 | Must execute at least once |
| Enhanced `for` | Automatically | Depends on collection | Arrays/Collections |

---

# 12. `for` vs `while`

## `for`

```java
for (int i = 0; i < 10; i++) {
    System.out.println(i);
}
```

Best when initialization, condition, and increment are closely related.

## `while`

```java
int i = 0;

while (i < 10) {
    System.out.println(i);
    i++;
}
```

Best when the number of iterations depends mainly on a condition.

---

# 13. `while` vs `do-while`

## `while`

Condition is checked first.

```java
int i = 10;

while (i < 5) {
    System.out.println(i);
}
```

Output:

```text
No output
```

## `do-while`

Body executes first.

```java
int i = 10;

do {
    System.out.println(i);
} while (i < 5);
```

Output:

```text
10
```

### Key Difference

```text
while
  ↓
Check condition
  ↓
Execute body

do-while
  ↓
Execute body
  ↓
Check condition
```

---

# 14. Infinite Loop

An infinite loop continues indefinitely because its condition never becomes false.

Example:

```java
while (true) {
    System.out.println("Running");
}
```

Another example:

```java
for (;;) {
    System.out.println("Running");
}
```

Avoid infinite loops unless they are intentionally required.

---

# 15. Nested Selenium Loop Example

Suppose you need to iterate through rows and columns of a table.

```java
List<WebElement> rows =
        driver.findElements(By.xpath("//table/tbody/tr"));

for (WebElement row : rows) {

    List<WebElement> columns =
            row.findElements(By.tagName("td"));

    for (WebElement column : columns) {
        System.out.println(column.getText());
    }
}
```

This uses a **nested enhanced for loop**.

---

# 16. Interview Answer

If an interviewer asks:

**"What are looping statements in Java?"**

You can answer:

> Java provides `for`, `while`, and `do-while` loops, along with the enhanced `for-each` loop. A `for` loop is generally used when the number of iterations is known. A `while` loop is useful when the condition determines how long the loop runs. A `do-while` loop executes at least once because its condition is checked after the loop body. The enhanced `for` loop is commonly used to iterate through arrays and collections.

---

# 17. Easy Way to Remember

```text
for       → Known iterations
while     → Condition first
do-while  → Execute first, condition later
for-each  → Arrays / Collections
```

---

# 18. Selenium Interview Focus

For Selenium automation interviews, pay special attention to:

```text
List<WebElement>
      ↓
findElements()
      ↓
Enhanced for loop
      ↓
Check each element
      ↓
Perform action
```

Example:

```java
List<WebElement> elements =
        driver.findElements(By.tagName("button"));

for (WebElement element : elements) {

    if (element.getText().equals("Login")) {
        element.click();
        break;
    }
}
```

This is a practical example of how Java looping is used in Selenium automation.

---

# Quick Revision

| Concept | Key Point |
|---|---|
| `for` | Best for known iterations |
| `while` | Checks condition before execution |
| `do-while` | Executes at least once |
| Enhanced `for` | Used with arrays/collections |
| `break` | Terminates the loop |
| `continue` | Skips current iteration |
| Nested loop | Loop inside another loop |
| Infinite loop | Condition never becomes false |
| Selenium | Commonly used with `List<WebElement>` |

## One-Line Definitions

> **for:** Executes code repeatedly based on initialization, condition, and increment/decrement.

> **while:** Executes code repeatedly while a condition remains true.

> **do-while:** Executes the code at least once and then checks the condition.

> **for-each:** Iterates through elements of an array or collection.
