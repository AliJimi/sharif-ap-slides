---
marp: true
theme: default
paginate: true
backgroundColor: #ffffff
color: #000000
header: "![height:25](assets/sharif-logo-blue.png) **Advanced Programming (AP) — Java Introduction**"
footer: "**Sharif University of Technology** • Fall 2025 • Mr. Ali Najimi • Hossein Masihi"
style: |
  :root { --brand: #1966ab; --text: #000000; }
  section { background-color: #ffffff; color: var(--text); font-size: 28px; font-family: "Inter","Segoe UI","Roboto","Helvetica Neue",Arial,sans-serif; }
  h1, h2, h3 { color: var(--brand); font-family: "Inter","Segoe UI","Roboto","Helvetica Neue",Arial,sans-serif; }
  .cols { display: grid; grid-template-columns: 1.35fr 0.9fr; gap: 28px; align-items: start; }
  .imgbox { border: 1px solid #eee; padding: 8px; border-radius: 10px; }
  .pill { display:inline-block; padding: 4px 10px; border:1px solid var(--brand); border-radius:999px; color: var(--brand); font-size:20px; }
  section.lead header, section.lead footer { display: none !important; }
  .timeline { display: flex; justify-content: space-between; align-items: center; margin-top: 60px; position: relative; }
  .timeline::before { content: ""; position: absolute; top: 50%; left: 0; width: 100%; height: 4px; background: #1966ab; }
  .point { text-align: center; position: relative; width: 150px; }
  .circle { width: 22px; height: 22px; border: 3px solid #1966ab; background: #fff; border-radius: 50%; margin: 0 auto 10px; }
  h3 { color: #1966ab; margin-bottom: 6px; }
---
<!-- _class: lead -->

![bg right:30% 90%](./assets/sharif-logo-blue.png)

# Advanced Programming
## Java Basics

**Instructor:** Ali Najimi
**Author:** Hossein Masihi
**Department of Computer Engineering**
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
---
```java
int age = 21;
double pi = 3.14;
boolean active = true;
char grade = 'A';
long big = 3_000_000_000L;
float ratio = 0.75f;
byte b = 127;
short s = 32000;
```

---

## Variables

* Variables store data in memory.
* Syntax:

    ```java
    type name = value;
    ```
---
* Example:

    ```java
    String name = "Advanced Programming!";
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