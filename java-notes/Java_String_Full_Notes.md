# String in Java — Complete Notes

## 1. Introduction

A `String` in Java is an object used to represent a sequence of characters.

```java
String name = "Siva";
System.out.println(name);
```

Output:
```text
Siva
```

`String` belongs to the `java.lang` package, so it does not need to be explicitly imported.

---

## 2. Characteristics of String

- `String` is a class.
- String objects are immutable.
- String literals are stored in the String Pool.
- String provides many built-in methods.
- `String` is a final class.
- String indexing starts from `0`.

Example:

```java
String text = "Java";
```

Indexes:

```text
J   a   v   a
0   1   2   3
```

---

## 3. Creating Strings

### 3.1 String Literal

```java
String language = "Java";
```

Example:

```java
String a = "Java";
String b = "Java";

System.out.println(a == b);
```

Output:

```text
true
```

### 3.2 Using `new`

```java
String language = new String("Java");
```

Example:

```java
String a = new String("Java");
String b = new String("Java");

System.out.println(a == b);
System.out.println(a.equals(b));
```

Output:

```text
false
true
```

`==` compares references, while `equals()` compares content.

---

## 4. String Pool

The String Pool stores shared String literals so that identical literals can be reused.

```java
String a = "Java";
String b = "Java";
```

Conceptually:

```text
a ──┐
    ├──> "Java"
b ──┘
```

Using `new String("Java")` creates a separate String object.

---

## 5. String Immutability

Strings are immutable. Once a String object is created, its content cannot be changed.

```java
String name = "Siva";

name.concat(" R");

System.out.println(name);
```

Output:

```text
Siva
```

To store the new value:

```java
name = name.concat(" R");

System.out.println(name);
```

Output:

```text
Siva R
```

The original String was not modified; a new String value was assigned.

---

## 6. Why String Is Immutable

String immutability provides benefits such as:

- Security
- String Pool sharing
- Thread safety
- Stable hash codes
- Predictable behavior
- Safe use as keys in collections such as `HashMap`

---

## 7. String Comparison

### `==`

Compares object references.

```java
String a = new String("Java");
String b = new String("Java");

System.out.println(a == b);
```

Output:

```text
false
```

### `equals()`

Compares String contents.

```java
String a = new String("Java");
String b = new String("Java");

System.out.println(a.equals(b));
```

Output:

```text
true
```

### `equalsIgnoreCase()`

Compares content without considering case.

```java
String a = "Java";
String b = "JAVA";

System.out.println(a.equalsIgnoreCase(b));
```

Output:

```text
true
```

---

# 8. Common String Methods

## `length()`

```java
String text = "Hello Java";
System.out.println(text.length());
```

Output: `10`

## `charAt()`

```java
String text = "Java";
System.out.println(text.charAt(0));
```

Output: `J`

## `toUpperCase()`

```java
System.out.println("hello java".toUpperCase());
```

Output: `HELLO JAVA`

## `toLowerCase()`

```java
System.out.println("HELLO JAVA".toLowerCase());
```

Output: `hello java`

## `contains()`

```java
String text = "Selenium with Java";
System.out.println(text.contains("Java"));
```

Output: `true`

## `startsWith()`

```java
String text = "Selenium Java";
System.out.println(text.startsWith("Selenium"));
```

Output: `true`

## `endsWith()`

```java
String text = "Selenium Java";
System.out.println(text.endsWith("Java"));
```

Output: `true`

## `substring()`

```java
String text = "Hello Java";

System.out.println(text.substring(6));
System.out.println(text.substring(0, 5));
```

Output:

```text
Java
Hello
```

The ending index is exclusive.

## `indexOf()`

```java
String text = "Hello Java";
System.out.println(text.indexOf("Java"));
```

Output: `6`

## `lastIndexOf()`

```java
String text = "Java is Java";
System.out.println(text.lastIndexOf("Java"));
```

Output: `8`

## `replace()`

```java
String text = "Hello Java";
System.out.println(text.replace("Java", "Selenium"));
```

Output: `Hello Selenium`

## `replaceAll()`

Uses regular expressions.

```java
String text = "Java123";
System.out.println(text.replaceAll("[0-9]", ""));
```

Output: `Java`

## `trim()`

Removes leading and trailing whitespace.

```java
String text = "   Hello Java   ";
System.out.println(text.trim());
```

Output: `Hello Java`

## `isEmpty()`

```java
String text = "";
System.out.println(text.isEmpty());
```

Output: `true`

## `isBlank()`

Checks whether a String is empty or contains only whitespace. Available since Java 11.

```java
String text = "   ";
System.out.println(text.isBlank());
```

Output: `true`

## `concat()`

```java
String result = "Hello ".concat("Java");
System.out.println(result);
```

Output: `Hello Java`

## `split()`

```java
String text = "Java,Selenium,TestNG";

String[] tools = text.split(",");

for (String tool : tools) {
    System.out.println(tool);
}
```

Output:

```text
Java
Selenium
TestNG
```

## `toCharArray()`

```java
String text = "Java";
char[] characters = text.toCharArray();

for (char ch : characters) {
    System.out.println(ch);
}
```

## `valueOf()`

```java
int number = 100;
String text = String.valueOf(number);
```

## `compareTo()`

```java
String a = "Java";
String b = "Java";

System.out.println(a.compareTo(b));
```

Output: `0`

Results:

- `0` → equal
- Negative → first String comes before second
- Positive → first String comes after second

---

# 9. String Method Quick Reference

| Method | Purpose |
|---|---|
| `length()` | Returns length |
| `charAt()` | Gets character at index |
| `equals()` | Compares content |
| `equalsIgnoreCase()` | Compares ignoring case |
| `contains()` | Checks for text |
| `startsWith()` | Checks beginning |
| `endsWith()` | Checks ending |
| `substring()` | Extracts part |
| `indexOf()` | Finds first occurrence |
| `lastIndexOf()` | Finds last occurrence |
| `toUpperCase()` | Converts to uppercase |
| `toLowerCase()` | Converts to lowercase |
| `trim()` | Removes leading/trailing whitespace |
| `isEmpty()` | Checks zero length |
| `isBlank()` | Checks empty/whitespace |
| `replace()` | Replaces text |
| `replaceAll()` | Replaces using regex |
| `concat()` | Joins Strings |
| `split()` | Splits into an array |
| `toCharArray()` | Converts to character array |
| `valueOf()` | Converts value to String |
| `compareTo()` | Lexicographical comparison |

---

# 10. String Types

Three commonly discussed Java classes for character sequences are:

1. `String`
2. `StringBuffer`
3. `StringBuilder`

## String

Immutable:

```java
String text = "Java";
text = text + " Selenium";
```

## StringBuffer

Mutable and synchronized:

```java
StringBuffer text = new StringBuffer("Hello");
text.append(" Java");

System.out.println(text);
```

Output:

```text
Hello Java
```

Common methods:

```text
append()
insert()
delete()
replace()
reverse()
```

## StringBuilder

Mutable and not synchronized:

```java
StringBuilder text = new StringBuilder("Hello");
text.append(" Java");

System.out.println(text);
```

Output:

```text
Hello Java
```

`StringBuilder` is generally preferred for frequent modifications in single-threaded code.

---

# 11. String vs StringBuffer vs StringBuilder

| Feature | String | StringBuffer | StringBuilder |
|---|---|---|---|
| Mutable | No | Yes | Yes |
| Immutable | Yes | No | No |
| Synchronized | Not applicable | Yes | No |
| Thread-safe | Yes, due to immutability | Yes | No |
| Modification performance | Lower for repeated changes | Moderate | Generally faster |
| Best use | Fixed text | Mutable text requiring synchronization | Frequent modifications |

---

# 12. Escape Characters

| Escape | Meaning |
|---|---|
| `\n` | New line |
| `\t` | Tab |
| `\"` | Double quote |
| `\'` | Single quote |
| `\\` | Backslash |
| `\r` | Carriage return |
| `\b` | Backspace |
| `\f` | Form feed |

Example:

```java
System.out.println("Hello\nJava");
```

Output:

```text
Hello
Java
```

---

# 13. String Formatting

```java
String name = "Siva";
int age = 30;

String result = String.format(
    "Name: %s, Age: %d",
    name,
    age
);

System.out.println(result);
```

Output:

```text
Name: Siva, Age: 30
```

Common format specifiers:

| Specifier | Meaning |
|---|---|
| `%s` | String |
| `%d` | Integer |
| `%f` | Floating-point |
| `%c` | Character |
| `%b` | Boolean |

---

# 14. Converting Between String and Primitive Types

## String to int

```java
String value = "100";
int number = Integer.parseInt(value);
```

## int to String

```java
int number = 100;
String value = String.valueOf(number);
```

## String to double

```java
String value = "10.50";
double number = Double.parseDouble(value);
```

## String to boolean

```java
String value = "true";
boolean result = Boolean.parseBoolean(value);
```

---

# 15. String and Character Array

String to character array:

```java
String text = "Java";
char[] chars = text.toCharArray();
```

Character array to String:

```java
char[] chars = {'J', 'a', 'v', 'a'};
String text = new String(chars);

System.out.println(text);
```

Output:

```text
Java
```

---

# 16. Null, Empty, and Blank Strings

## Null

```java
String text = null;
```

The variable does not reference a String object.

Calling a method can cause `NullPointerException`.

## Empty

```java
String text = "";
```

The String exists but has zero characters.

```java
System.out.println(text.isEmpty());
```

Output: `true`

## Blank

```java
String text = "   ";
```

It contains whitespace.

```java
System.out.println(text.isBlank());
```

Output: `true`

---

# 17. Null-Safe Comparison

Avoid:

```java
String username = null;

if (username.equals("admin")) {
    System.out.println("Valid");
}
```

This can cause `NullPointerException`.

Prefer:

```java
if ("admin".equals(username)) {
    System.out.println("Valid");
}
```

---

# 18. Common String Programs

## Reverse a String

```java
String text = "Java";

String reversed = new StringBuilder(text)
        .reverse()
        .toString();

System.out.println(reversed);
```

Output:

```text
avaJ
```

## Check Palindrome

```java
String text = "madam";

String reversed = new StringBuilder(text)
        .reverse()
        .toString();

if (text.equals(reversed)) {
    System.out.println("Palindrome");
} else {
    System.out.println("Not a palindrome");
}
```

Output:

```text
Palindrome
```

## Count Characters

```java
String text = "Java";

System.out.println(text.length());
```

Output:

```text
4
```

## Count a Specific Character

```java
String text = "banana";
char target = 'a';

int count = 0;

for (int i = 0; i < text.length(); i++) {
    if (text.charAt(i) == target) {
        count++;
    }
}

System.out.println(count);
```

Output:

```text
3
```

---

# 19. String in Selenium Automation

Strings are heavily used in Selenium for validations and test data.

## Validate Page Title

```java
String actualTitle = driver.getTitle();
String expectedTitle = "Amazon";

if (actualTitle.equals(expectedTitle)) {
    System.out.println("Title is correct");
} else {
    System.out.println("Title is incorrect");
}
```

## Get Text From an Element

```java
String actualMessage =
        driver.findElement(By.id("message")).getText();

System.out.println(actualMessage);
```

## Validate Text Using `contains()`

```java
String actualMessage =
        driver.findElement(By.id("message")).getText();

if (actualMessage.contains("Success")) {
    System.out.println("Test Passed");
}
```

## Validate Attribute Value

```java
String value =
        driver.findElement(By.id("username"))
              .getAttribute("value");

if ("Siva".equals(value)) {
    System.out.println("Username is correct");
}
```

---

# 20. Important String Methods for Selenium

```text
equals()
equalsIgnoreCase()
contains()
startsWith()
endsWith()
trim()
isEmpty()
isBlank()
substring()
replace()
split()
toUpperCase()
toLowerCase()
```

Example:

```java
String actualText =
        driver.findElement(By.id("message"))
              .getText()
              .trim();

if (actualText.equals("Login Successful")) {
    System.out.println("Test Passed");
}
```

---

# 21. String Interview Questions

### Q1. What is String in Java?

`String` is a class in `java.lang` used to represent a sequence of characters. String objects are immutable.

### Q2. Is String a primitive data type?

No. `String` is a reference type/class, not a primitive data type.

### Q3. Why is String immutable?

Immutability provides security, String Pool sharing, thread-safety benefits, and stable hash codes.

### Q4. Difference between `==` and `equals()`?

- `==` compares references.
- `equals()` compares content.

```java
String a = new String("Java");
String b = new String("Java");

System.out.println(a == b);       // false
System.out.println(a.equals(b));  // true
```

### Q5. What is String Pool?

String Pool is a pool of shared String literals maintained by the JVM to reduce duplicate String objects.

### Q6. Difference between String and StringBuilder?

`String` is immutable. `StringBuilder` is mutable and is useful for repeated String modifications.

### Q7. Difference between StringBuilder and StringBuffer?

`StringBuilder` is mutable and not synchronized. `StringBuffer` is mutable and synchronized.

### Q8. Can String be extended?

No. `String` is a `final` class.

### Q9. How do you reverse a String?

```java
String text = "Java";

String reversed = new StringBuilder(text)
        .reverse()
        .toString();
```

### Q10. How do you compare Strings ignoring case?

```java
a.equalsIgnoreCase(b);
```

---

# 22. Quick Revision

## String Creation

```java
String a = "Java";
String b = new String("Java");
```

## Comparison

```java
a.equals(b);
a.equalsIgnoreCase(b);
a == b;
```

## Important Methods

```text
length()
charAt()
substring()
indexOf()
lastIndexOf()
contains()
startsWith()
endsWith()
equals()
equalsIgnoreCase()
toUpperCase()
toLowerCase()
trim()
isEmpty()
isBlank()
replace()
replaceAll()
concat()
split()
toCharArray()
valueOf()
compareTo()
```

## Mutable Alternatives

```java
StringBuilder
StringBuffer
```

## Key Interview Points

- `String` is a class.
- `String` is immutable.
- String literals use the String Pool.
- `==` compares references.
- `equals()` compares content.
- `StringBuilder` is mutable and not synchronized.
- `StringBuffer` is mutable and synchronized.
- Use `StringBuilder` for frequent String modifications in typical single-threaded code.
- Strings are heavily used in Selenium for page-title, text, attribute, and test-data validation.
