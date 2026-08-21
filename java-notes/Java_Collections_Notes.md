# Collections in Java

## 1. Introduction

The **Java Collections Framework (JCF)** is a set of interfaces, classes, and methods used to store, manipulate, and process groups of objects.

Collections are very important in **QA Automation/Selenium** because they are frequently used for:

- Storing web elements
- Managing test data
- Handling API responses
- Removing duplicate values
- Storing key-value data
- Sorting and filtering data

---

## 2. Java Collections Hierarchy

```text
                    Iterable
                       |
                  Collection
             __________|__________
            |          |          |
          List        Set       Queue
            |          |          |
      ArrayList     HashSet    PriorityQueue
      LinkedList    LinkedHashSet
      Vector        TreeSet
      Stack

                    Map
                     |
          ______________________
         |          |           |
      HashMap   LinkedHashMap  TreeMap
```

> **Important:** `Map` is part of the Java Collections Framework, but it does **not** extend the `Collection` interface.

---

# 3. List

A `List` is an **ordered collection**.

### Characteristics

- Maintains insertion order
- Allows duplicate elements
- Allows index-based access
- Can contain multiple `null` values

### Example

```java
List<String> names = new ArrayList<>();

names.add("Siva");
names.add("Rahul");
names.add("John");
names.add("Siva");

System.out.println(names);
```

Output:

```text
[Siva, Rahul, John, Siva]
```

## Common List Implementations

### ArrayList

`ArrayList` is generally preferred when frequent access by index is required.

```java
ArrayList<String> names = new ArrayList<>();

names.add("Siva");
names.add("Rahul");
names.add("John");

System.out.println(names.get(0));
```

Output:

```text
Siva
```

### LinkedList

`LinkedList` is useful for queue/deque operations and scenarios involving frequent structural changes.

```java
LinkedList<String> names = new LinkedList<>();

names.add("Siva");
names.add("Rahul");

names.addFirst("John");
names.addLast("Kumar");

System.out.println(names);
```

### Vector

`Vector` is a legacy synchronized implementation of `List`.

```java
Vector<String> names = new Vector<>();

names.add("Siva");
names.add("Rahul");
```

Generally, prefer `ArrayList` unless the legacy synchronization behavior of `Vector` is specifically required.

### Stack

`Stack` represents a **LIFO (Last-In-First-Out)** structure.

```java
Stack<String> stack = new Stack<>();

stack.push("A");
stack.push("B");
stack.push("C");

System.out.println(stack.pop());
```

Output:

```text
C
```

---

# 4. Set

A `Set` is used when you need **unique elements**.

### Characteristics

- Does not allow duplicates
- Usually does not provide index-based access
- Ordering depends on the implementation

## HashSet

`HashSet` does not guarantee insertion order.

```java
HashSet<String> names = new HashSet<>();

names.add("Siva");
names.add("Rahul");
names.add("Siva");

System.out.println(names);
```

The duplicate `"Siva"` is ignored.

## LinkedHashSet

`LinkedHashSet` maintains insertion order.

```java
LinkedHashSet<String> names = new LinkedHashSet<>();

names.add("Siva");
names.add("Rahul");
names.add("John");

System.out.println(names);
```

Output:

```text
[Siva, Rahul, John]
```

## TreeSet

`TreeSet` stores elements in sorted order.

```java
TreeSet<Integer> numbers = new TreeSet<>();

numbers.add(50);
numbers.add(10);
numbers.add(30);
numbers.add(20);

System.out.println(numbers);
```

Output:

```text
[10, 20, 30, 50]
```

---

# 5. Queue

A `Queue` is generally used for processing elements in **FIFO (First-In-First-Out)** order.

```java
Queue<String> queue = new LinkedList<>();

queue.add("Siva");
queue.add("Rahul");
queue.add("John");

System.out.println(queue.poll());
```

Output:

```text
Siva
```

## Common Queue Methods

| Method | Purpose |
|---|---|
| `add()` | Adds an element |
| `offer()` | Adds an element |
| `poll()` | Removes and returns the first element |
| `peek()` | Returns the first element without removing it |

---

# 6. PriorityQueue

`PriorityQueue` processes elements according to their priority/natural ordering.

```java
PriorityQueue<Integer> numbers = new PriorityQueue<>();

numbers.add(50);
numbers.add(10);
numbers.add(30);

System.out.println(numbers.poll());
```

Output:

```text
10
```

---

# 7. Map

A `Map` stores data as **key-value pairs**.

```text
Key → Value

101 → Siva
102 → Rahul
103 → John
```

A key must be unique.

## HashMap

`HashMap` is the most commonly used `Map` implementation.

```java
HashMap<Integer, String> employees = new HashMap<>();

employees.put(101, "Siva");
employees.put(102, "Rahul");
employees.put(103, "John");

System.out.println(employees.get(101));
```

Output:

```text
Siva
```

### Important HashMap Methods

```java
put()
get()
remove()
containsKey()
containsValue()
keySet()
values()
entrySet()
```

Example:

```java
System.out.println(employees.containsKey(101));
System.out.println(employees.containsValue("Siva"));
```

---

# 8. LinkedHashMap

`LinkedHashMap` maintains insertion order.

```java
LinkedHashMap<Integer, String> employees = new LinkedHashMap<>();

employees.put(101, "Siva");
employees.put(102, "Rahul");
employees.put(103, "John");

System.out.println(employees);
```

---

# 9. TreeMap

`TreeMap` stores entries according to sorted key order.

```java
TreeMap<Integer, String> employees = new TreeMap<>();

employees.put(103, "John");
employees.put(101, "Siva");
employees.put(102, "Rahul");

System.out.println(employees);
```

Output:

```text
{101=Siva, 102=Rahul, 103=John}
```

---

# 10. HashMap vs LinkedHashMap vs TreeMap

| Feature | HashMap | LinkedHashMap | TreeMap |
|---|---|---|---|
| Ordering | No guaranteed order | Insertion order | Sorted key order |
| Performance | Generally fastest | Slightly slower than HashMap | Generally slower |
| Duplicate keys | Not allowed | Not allowed | Not allowed |
| Null key | One allowed | One allowed | Generally not allowed |
| Main use case | General key-value storage | Preserve insertion order | Sorted keys |

---

# 11. ArrayList vs LinkedList

| Feature | ArrayList | LinkedList |
|---|---|---|
| Internal structure | Dynamic array | Doubly linked list |
| Random access | Fast | Slow |
| Insertion/deletion | Generally slower for middle positions | Generally better for structural changes once the position/node is reached |
| Memory | Lower | Higher |
| Common use | General-purpose List | Queue/deque and structural changes |

### Interview Answer

> ArrayList is generally preferred when we frequently access elements by index, while LinkedList is useful when the data structure requires frequent insertion/removal operations, especially at the ends.

---

# 12. ArrayList vs HashSet

| Feature | ArrayList | HashSet |
|---|---|---|
| Duplicates | Allowed | Not allowed |
| Order | Insertion order | No guaranteed order |
| Index | Yes | No |
| Main use | Ordered data | Unique data |

### ArrayList Example

```java
List<String> list = new ArrayList<>();

list.add("Java");
list.add("Java");

System.out.println(list);
```

Output:

```text
[Java, Java]
```

### HashSet Example

```java
Set<String> set = new HashSet<>();

set.add("Java");
set.add("Java");

System.out.println(set);
```

Output:

```text
[Java]
```

---

# 13. Iterating Collections

## For Loop

```java
List<String> names = new ArrayList<>();

names.add("Siva");
names.add("Rahul");
names.add("John");

for (int i = 0; i < names.size(); i++) {
    System.out.println(names.get(i));
}
```

## Enhanced For Loop

```java
for (String name : names) {
    System.out.println(name);
}
```

## Iterator

```java
Iterator<String> iterator = names.iterator();

while (iterator.hasNext()) {
    System.out.println(iterator.next());
}
```

---

# 14. Iterating a Map

```java
Map<Integer, String> employees = new HashMap<>();

employees.put(101, "Siva");
employees.put(102, "Rahul");
employees.put(103, "John");

for (Map.Entry<Integer, String> entry : employees.entrySet()) {

    System.out.println(
        entry.getKey() + " = " + entry.getValue()
    );
}
```

Output:

```text
101 = Siva
102 = Rahul
103 = John
```

---

# 15. Collections Utility Class

Java provides the `Collections` utility class for operations such as sorting and reversing.

## Sorting

```java
List<Integer> numbers = new ArrayList<>();

numbers.add(50);
numbers.add(10);
numbers.add(30);
numbers.add(20);

Collections.sort(numbers);

System.out.println(numbers);
```

Output:

```text
[10, 20, 30, 50]
```

## Reverse

```java
Collections.reverse(numbers);

System.out.println(numbers);
```

---

# 16. Collections vs Collection

This is a common Java interview question.

## Collection

`Collection` is an **interface**.

```java
Collection<String> data;
```

It is the root interface for major collection types such as:

- `List`
- `Set`
- `Queue`

## Collections

`Collections` is a **utility class**.

```java
Collections.sort(list);
Collections.reverse(list);
```

### Easy Way to Remember

```text
Collection  → Interface
Collections → Utility Class
```

---

# 17. Selenium Example

Collections are heavily used in Selenium automation.

For example, getting all links from a webpage:

```java
List<WebElement> links = driver.findElements(By.tagName("a"));

for (WebElement link : links) {
    System.out.println(link.getText());
}
```

`findElements()` returns:

```java
List<WebElement>
```

You can also use a `Set` when you want unique values:

```java
Set<String> uniqueLinks = new HashSet<>();

for (WebElement link : links) {
    uniqueLinks.add(link.getText());
}
```

---

# 18. Real QA Automation Example — Remove Duplicate Test Data

```java
List<String> testData = Arrays.asList(
    "Login",
    "Search",
    "Login",
    "Checkout",
    "Search"
);

Set<String> uniqueTestData = new LinkedHashSet<>(testData);

System.out.println(uniqueTestData);
```

Output:

```text
[Login, Search, Checkout]
```

`LinkedHashSet` is useful because it removes duplicates while preserving the original insertion order.

---

# 19. Which Collection Should You Choose?

```text
Need ordered data + duplicates?
        ↓
      List
        ↓
    ArrayList

Need unique data?
        ↓
       Set
        ↓
    HashSet

Need unique data + insertion order?
        ↓
 LinkedHashSet

Need unique data + sorted order?
        ↓
    TreeSet

Need key-value pairs?
        ↓
       Map
        ↓
    HashMap

Need key-value + insertion order?
        ↓
 LinkedHashMap

Need key-value + sorted keys?
        ↓
    TreeMap

Need FIFO processing?
        ↓
      Queue
```

---

# 20. Important Collections for Java Interviews

Focus especially on:

1. `ArrayList`
2. `LinkedList`
3. `HashSet`
4. `LinkedHashSet`
5. `TreeSet`
6. `HashMap`
7. `LinkedHashMap`
8. `TreeMap`
9. `Queue`
10. `PriorityQueue`
11. `Iterator`
12. `Comparable`
13. `Comparator`
14. `Collections` utility class

---

# 21. Collections in QA Automation

For Selenium + Java automation, these are particularly important:

| Collection | Typical QA Automation Usage |
|---|---|
| `List<WebElement>` | Store multiple web elements |
| `ArrayList<String>` | Store test data |
| `Set<String>` | Remove duplicate values |
| `HashSet<String>` | Validate uniqueness |
| `Map<String, String>` | Store key-value test data |
| `HashMap<String, String>` | Test configuration/data |
| `Iterator` | Iterate through collection values |
| `LinkedHashSet` | Remove duplicates while preserving order |

---

# 22. Interview Questions

### Beginner

1. What is Collection in Java?
2. What is the Java Collections Framework?
3. What is the difference between Collection and Collections?
4. What is the difference between List, Set, and Map?
5. Does Map extend Collection?
6. What is ArrayList?
7. What is HashSet?
8. What is HashMap?

### Intermediate

9. ArrayList vs LinkedList?
10. ArrayList vs HashSet?
11. HashSet vs LinkedHashSet?
12. HashSet vs TreeSet?
13. HashMap vs LinkedHashMap?
14. HashMap vs TreeMap?
15. How does HashMap work?
16. How do you remove duplicates from a List?
17. How do you iterate through a Map?
18. What is Iterator?

### QA/Selenium

19. What is the return type of `findElements()`?
20. How do you store multiple Selenium WebElements?
21. How would you remove duplicate test data?
22. How would you store key-value test data?
23. How would you compare two lists?
24. How would you find duplicate values in a collection?
25. How would you sort test data?

---

# 23. Quick Revision

```text
LIST
 ├── ArrayList
 ├── LinkedList
 ├── Vector
 └── Stack

SET
 ├── HashSet
 ├── LinkedHashSet
 └── TreeSet

QUEUE
 └── PriorityQueue

MAP
 ├── HashMap
 ├── LinkedHashMap
 └── TreeMap
```

### Remember

```text
List → Ordered + Duplicates
Set  → Unique
Queue → FIFO/Priority processing
Map  → Key + Value
```

### Most Important for Selenium

```text
List<WebElement>
ArrayList
HashSet
LinkedHashSet
HashMap
Map
Iterator
```
