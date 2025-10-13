---
marp: true
theme: default
paginate: true
backgroundColor: #ffffff
color: #000000
header: "![height:24](/assests/sharif-logo-blue.png) **Advanced Programming (AP) — Java Basics**"
footer: "**Sharif University of Technology** • Fall 2025 • Dr. Ali Najimi • Hossein Masihi"
style: |
  :root { --brand: #1966ab; --text: #000000; }
  section { background-color: #ffffff; color: var(--text); font-size: 28px; font-family: 'Inter','Segoe UI','Roboto','Helvetica Neue',Arial,sans-serif; }
  h1, h2, h3 { color: var(--brand); font-family: 'Inter','Segoe UI','Roboto','Helvetica Neue',Arial,sans-serif; }
  ul { margin-top: 10px; }
---

# Advanced Programming
## Java Basics

**Teacher:** Dr. Ali Najimi**  
**Writer:** Hossein Masihi**  
**Sharif University of Technology**  
**Fall 2025**

---

## Primitive Data Types

* Java has **8 primitive types**:
  * `byte`, `short`, `int`, `long` → integers  
  * `float`, `double` → decimals  
  * `char` → single character (Unicode)  
  * `boolean` → true/false
* Each has a fixed size (e.g., `int` = 4 bytes, `double` = 8 bytes)

```java
int age = 21;
double pi = 3.14;
boolean active = true;
char grade = 'A';
long big = 3_000_000_000L;
float ratio = 0.75f;
byte b = 127;
short s = 32000;
````

---

## Variables

* Variables store data in memory.
* Syntax:

```java
type name = value;
```

* Example:

```java
String name = "Hossein";
int year = 2025;
```

* **Rules:**

  * Must start with letter or underscore.
  * Case-sensitive.
  * Cannot be a reserved keyword.

---

## Methods

* Methods define reusable blocks of code.

```java
returnType name(parameters) {
    // body
}
```

* Example:

```java
int sum(int a, int b) {
    return a + b;
}
```

* **Benefits:** Code reusability, readability, and structure.

---

## Controllers: if, while, switch, for

* Control the flow of execution.

```java
if (x > 10) System.out.println("Big");
else System.out.println("Small");
```

```java
for (int i = 0; i < 5; i++) {
    System.out.println(i);
}
```

```java
switch (day) {
    case 1: System.out.println("Monday"); break;
    default: System.out.println("Unknown");
}
```

---

## Strings

* A `String` is a sequence of characters.
* Stored as an **immutable** object.
* Common methods:

  * `length()`, `substring()`, `equals()`, `concat()`

```java
String s = "Sharif";
System.out.println(s.toUpperCase());
```

* Immutable means: once created, cannot be changed.

---

## Arrays

* Arrays store multiple values of the same type.

```java
int[] nums = {10, 20, 30};
```

* Access with index: `nums[0]`
* Loop example:

```java
for (int n : nums) {
    System.out.println(n);
}
```

* Multidimensional:

```java
int[][] matrix = {{1, 2}, {3, 4}};
```

---

## Example: Combining Concepts

```java
public class Example {
    public static void main(String[] args) {
        int[] numbers = {2, 4, 6, 8};
        for (int n : numbers) {
            if (n % 4 == 0) {
                System.out.println(n + " is divisible by 4");
            }
        }
    }
}
```

* Demonstrates variables, arrays, loops, and conditionals.

---

## Best Practices

* Use descriptive names (`studentAge`, not `a1`).
* Avoid magic numbers → use constants.
* Keep methods short and focused.
* Use consistent indentation and comments.

```java
// Bad
int a1=21; if(a1>18){System.out.println("ok");}

// Good
final int ADULT_AGE = 18;
int studentAge = 21;
if (studentAge > ADULT_AGE) {
    System.out.println("ok");
}
```

---

# Thank You 🙌

**Good luck and happy coding!**
*Advanced Programming – Fall 2025 – Sharif University of Technology*