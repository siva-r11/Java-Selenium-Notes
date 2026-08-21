# Array in Java

An **array** in Java is a fixed-size data structure used to store **multiple values of the same data type** in a single variable.

For example, instead of:

```java
int mark1 = 80;
int mark2 = 90;
int mark3 = 75;
```

you can use:

```java
int[] marks = {80, 90, 75};
```

---

## 1. Declaring an Array

### Syntax

```java
dataType[] arrayName;
```

Example:

```java
int[] numbers;
String[] names;
```

You can also write:

```java
int numbers[];
```

The recommended Java style is:

```java
int[] numbers;
```

---

## 2. Creating an Array

Use the `new` keyword:

```java
int[] numbers = new int[5];
```

This creates an array that can store **5 integers**.

The indexes are:

```text
Index:   0   1   2   3   4
         ↓   ↓   ↓   ↓   ↓
Value:  [ ] [ ] [ ] [ ] [ ]
```

Java array indexes start from **0**.

---

## 3. Initializing an Array

You can initialize an array directly:

```java
int[] numbers = {10, 20, 30, 40, 50};
```

Indexes:

```text
10 → index 0
20 → index 1
30 → index 2
40 → index 3
50 → index 4
```

---

## 4. Accessing Array Elements

Use the index:

```java
int[] numbers = {10, 20, 30, 40, 50};

System.out.println(numbers[0]);
System.out.println(numbers[2]);
System.out.println(numbers[4]);
```

Output:

```text
10
30
50
```

---

## 5. Updating Array Elements

You can change an existing value:

```java
int[] numbers = {10, 20, 30};

numbers[1] = 100;

System.out.println(numbers[1]);
```

Output:

```text
100
```

The array becomes:

```text
[10, 100, 30]
```

---

## 6. Array Length

Use the `.length` property to get the size of an array.

```java
int[] numbers = {10, 20, 30, 40, 50};

System.out.println(numbers.length);
```

Output:

```text
5
```

Important:

```java
array.length
```

not:

```java
array.length()
```

`length` is a property, not a method.

---

## 7. Loop Through an Array

### Using `for` Loop

```java
int[] numbers = {10, 20, 30, 40, 50};

for (int i = 0; i < numbers.length; i++) {
    System.out.println(numbers[i]);
}
```

Output:

```text
10
20
30
40
50
```

---

## 8. Enhanced `for` Loop

The enhanced `for` loop is easier when you simply need each value.

```java
int[] numbers = {10, 20, 30, 40, 50};

for (int number : numbers) {
    System.out.println(number);
}
```

Output:

```text
10
20
30
40
50
```

### Syntax

```java
for (dataType variable : array) {
    // code
}
```

---

## 9. String Array

Arrays can store objects such as `String`.

```java
String[] browsers = {
    "Chrome",
    "Firefox",
    "Edge"
};
```

Loop:

```java
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

---

## 10. Array of Objects

An array can also store object references.

```java
Employee[] employees = new Employee[3];
```

Example:

```java
class Employee {

    String name;

    Employee(String name) {
        this.name = name;
    }
}
```

Create objects:

```java
Employee[] employees = {
    new Employee("Siva"),
    new Employee("John"),
    new Employee("David")
};
```

Loop:

```java
for (Employee employee : employees) {
    System.out.println(employee.name);
}
```

---

## 11. Two-Dimensional Array

A two-dimensional array can be thought of as a **table with rows and columns**.

```java
int[][] numbers = {
    {10, 20, 30},
    {40, 50, 60},
    {70, 80, 90}
};
```

Structure:

```text
       Column
        0   1   2
       ┌───┬───┬───┐
Row 0  │10 │20 │30 │
       ├───┼───┼───┤
Row 1  │40 │50 │60 │
       ├───┼───┼───┤
Row 2  │70 │80 │90 │
       └───┴───┴───┘
```

Access:

```java
System.out.println(numbers[0][1]);
```

Output:

```text
20
```

---

## 12. Loop Through 2D Array

Use nested loops:

```java
int[][] numbers = {
    {10, 20, 30},
    {40, 50, 60},
    {70, 80, 90}
};

for (int i = 0; i < numbers.length; i++) {

    for (int j = 0; j < numbers[i].length; j++) {
        System.out.println(numbers[i][j]);
    }
}
```

---

## 13. Default Values of Arrays

When an array is created using `new`, Java automatically assigns default values.

### Integer

```java
int[] numbers = new int[3];
```

Result:

```text
[0, 0, 0]
```

### Boolean

```java
boolean[] values = new boolean[3];
```

Result:

```text
[false, false, false]
```

### String

```java
String[] names = new String[3];
```

Result:

```text
[null, null, null]
```

---

## 14. ArrayIndexOutOfBoundsException

Java arrays are zero-indexed.

If:

```java
int[] numbers = {10, 20, 30};
```

valid indexes are:

```text
0
1
2
```

This is invalid:

```java
System.out.println(numbers[3]);
```

It causes:

```text
ArrayIndexOutOfBoundsException
```

---

## 15. Array vs ArrayList

This is an important Java interview topic.

| Array | ArrayList |
|---|---|
| Fixed size | Dynamic size |
| Can store primitives | Stores objects/wrapper types |
| `length` | `size()` |
| Simple for fixed data | More flexible |
| `int[]` | `ArrayList<Integer>` |

Example:

```java
int[] numbers = {10, 20, 30};
```

ArrayList:

```java
ArrayList<Integer> numbers = new ArrayList<>();

numbers.add(10);
numbers.add(20);
numbers.add(30);
```

---

## 16. Selenium Example

Arrays are commonly used to store simple test data.

```java
String[] usernames = {
    "user1",
    "user2",
    "user3"
};

for (String username : usernames) {

    System.out.println("Testing user: " + username);
}
```

You can also store URLs:

```java
String[] urls = {
    "https://example.com",
    "https://google.com",
    "https://github.com"
};

for (String url : urls) {

    driver.get(url);

    System.out.println(driver.getTitle());
}
```

In larger automation frameworks, external test-data sources or TestNG data providers are often preferable for substantial datasets.

---

## 17. Selenium — Multiple Test Data

Example:

```java
String[] usernames = {
    "user1",
    "user2",
    "user3"
};

String[] passwords = {
    "pass1",
    "pass2",
    "pass3"
};

for (int i = 0; i < usernames.length; i++) {

    System.out.println(
        "Username: " + usernames[i] +
        " Password: " + passwords[i]
    );
}
```

Output:

```text
Username: user1 Password: pass1
Username: user2 Password: pass2
Username: user3 Password: pass3
```

---

## 18. Complete Selenium Example

```java
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;

public class ArrayExample {

    public static void main(String[] args) {

        WebDriver driver = new ChromeDriver();

        String[] urls = {
            "https://example.com",
            "https://google.com"
        };

        for (String url : urls) {

            driver.get(url);

            System.out.println(
                "URL: " + url
            );

            System.out.println(
                "Title: " + driver.getTitle()
            );
        }

        driver.quit();
    }
}
```

Here:

```text
String[] urls
     ↓
Array
     ↓
Stores multiple URLs
     ↓
for-each loop
     ↓
Opens each URL in Selenium
```

---

## 19. Important Array Methods

Arrays themselves have the `.length` property.

For additional operations, Java provides the `Arrays` utility class.

Import:

```java
import java.util.Arrays;
```

### Sort

```java
int[] numbers = {50, 20, 40, 10, 30};

Arrays.sort(numbers);

System.out.println(Arrays.toString(numbers));
```

Output:

```text
[10, 20, 30, 40, 50]
```

### Convert Array to String

```java
System.out.println(Arrays.toString(numbers));
```

### Compare Arrays

```java
Arrays.equals(array1, array2);
```

### Fill Array

```java
Arrays.fill(numbers, 100);
```

---

## 20. Important Interview Questions

1. What is an array in Java?
2. Why are arrays zero-indexed?
3. How do you declare an array?
4. How do you initialize an array?
5. How do you find the length of an array?
6. Can an array size be changed after creation?
7. What is `ArrayIndexOutOfBoundsException`?
8. What are the default values of array elements?
9. What is a multidimensional array?
10. What is the difference between an array and ArrayList?
11. Can an array store objects?
12. Can an array store primitive data types?
13. How do you loop through an array?
14. What is the difference between normal `for` and enhanced `for` loop?
15. How are arrays used in Selenium automation?

---

# Interview Answer

### What is an array in Java?

> An array is a fixed-size data structure used to store multiple values of the same type under a single variable name. Array indexing starts from zero, and the size is fixed once the array is created. Arrays can store primitive values as well as object references.

### Example

```java
int[] numbers = {10, 20, 30};
```

Here:

```text
numbers → Array reference
10      → Index 0
20      → Index 1
30      → Index 2
```

---

# Quick Revision

```text
Array
  ↓
Fixed-size collection
  ↓
Same data type
  ↓
Index starts from 0
  ↓
Use .length for size
```

### Example

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

### Selenium Connection

```text
String[] urls
     ↓
Multiple URLs
     ↓
for-each loop
     ↓
driver.get(url)
     ↓
Automate multiple pages
```

---

# One-Line Definition

> **An array in Java is a fixed-size collection that stores multiple values of the same type and accesses them using zero-based indexes.**
