---
marp: true
theme: default
paginate: true
backgroundColor: #ffffff
color: #000000
header: "![height:25](https://cdn.shraif.ir/cdn/main/ap/sharif-logo-blue.png) **Advanced Programming (AP) — Error Handling & Exception Management**"
footer: "**Sharif University of Technology** • Fall 2025 • Mr. Ali Najimi • Hossein Masihi"
style: |
  :root { --brand: #1966ab; --text: #000000; }
  section {
    background-color: #ffffff;
    color: var(--text);
    font-size: 28px;
    font-family: 'Inter','Segoe UI','Roboto','Helvetica Neue',Arial,sans-serif;
    animation: fadeIn 0.9s ease-in;
  }
  h1, h2, h3 {
    color: var(--brand);
    font-family: 'Inter','Segoe UI','Roboto','Helvetica Neue',Arial,sans-serif;
    animation: slideUp 0.8s ease-out;
  }
  ul, p, pre, table { animation: fadeIn 1s ease-in; }
  code { font-size: 90%; }
  .cols { display: grid; grid-template-columns: 1.4fr 0.6fr; gap: 24px; align-items: start; }
  .imgbox { border: 1px solid #eee; padding: 8px; border-radius: 10px; text-align:center; animation: zoomIn 1s ease-in; }
  .imgbox img { border-radius: 10px; border: 3px solid #1966ab; }
  .pill { display:inline-block; padding: 4px 10px; border:1px solid var(--brand); border-radius:999px; color: var(--brand); font-size:20px; }
  @keyframes fadeIn { from { opacity: 0; transform: translateY(10px);} to { opacity: 1; transform: translateY(0);} }
  @keyframes slideUp { from { opacity: 0; transform: translateY(20px);} to { opacity: 1; transform: translateY(0);} }
  @keyframes zoomIn { from { opacity: 0; transform: scale(0.9);} to { opacity: 1; transform: scale(1);} }
  section.lead header, section.lead footer { display: none !important; }
---

<!-- _class: lead -->
![bg right:30% 90%](https://cdn.shraif.ir/cdn/main/ap/sharif-logo-blue.png)
# Advanced Programming
## Error Handling & Exception Management in Java

**Instructor:** Ali Najimi  
**Author:** Hossein Masihi  
Sharif University of Technology — Fall 2025

---

# Table of Contents

1. Traditional Error Management  
2. Exception Handling in Java  
3. `try` / `catch` / `finally`  
4. Checked vs Unchecked Exceptions  
5. Runtime Exceptions  
6. Pros & Cons of Exception Systems  
7. Summary

---

# Before Exceptions — Traditional Error Management

```java
int divide(int a, int b) {
    if (b == 0) return -1; // error signal
    return a / b;
}
````

Problems:

* Error signals depend on **magic values**
* Hard to differentiate **valid output** from **error**
* No stack trace → debugging is difficult

> Traditional error codes are weak and unreliable.

---

# Exception Management in Java

Java introduced a **structured** error-handling system:

```java
try {
    // code that may fail
} catch (Exception e) {
    // handle the failure
}
```

Benefits:

* Clear separation of **normal flow** vs **error flow**
* Preserves stack trace → easier debugging
* Promotes predictable failure behavior

---

# `try` / `catch` / `finally`

```java
try {
    FileReader f = new FileReader("data.txt");
} catch (FileNotFoundException e) {
    System.out.println("File not found");
} finally {
    System.out.println("Cleanup always runs");
}
```

* `try` → code that may throw exception
* `catch` → handles specific failures
* `finally` → **always executes**, even if exception occurs

> Use `finally` for releasing resources (streams, DB connections, sockets).

---

# Checked vs Unchecked Exceptions

| Type          | Extends            | Must be handled?              | Examples                                   |
| ------------- | ------------------ | ----------------------------- | ------------------------------------------ |
| **Checked**   | `Exception`        | Yes (`try/catch` or `throws`) | `IOException`, `SQLException`              |
| **Unchecked** | `RuntimeException` | Optional                      | `NullPointerException`, `IndexOutOfBounds` |

> Checked exceptions enforce **compile-time safety**.

---

# Runtime Exceptions (Unchecked)

```java
int[] arr = new int[3];
arr[5] = 10; // throws ArrayIndexOutOfBoundsException
```

Common Runtime Exceptions:

* `NullPointerException`
* `IllegalArgumentException`
* `ArithmeticException`

Characteristics:

* Usually caused by **programming mistakes**
* Should be prevented, not caught silently

> Runtime Exceptions = *Fix the code, not the input.*

---

# Throwing Custom Exceptions

```java
class InvalidAgeException extends Exception {
    InvalidAgeException(String msg) { super(msg); }
}

void register(int age) throws InvalidAgeException {
    if (age < 18) throw new InvalidAgeException("Must be 18+");
}
```

> Custom exceptions improve clarity and domain expression.

---

# Pros & Cons of Exception System

| Pros                      | Cons                                               |
| ------------------------- | -------------------------------------------------- |
| Clear error propagation   | Misuse can lead to messy flow                      |
| Stack trace debugging     | Too many exception types confuse design            |
| Encourages robust design  | Overuse of checked exceptions can harm readability |
| Enables graceful recovery | Requires discipline and testing                    |

> Exceptions must be used **intentionally**, not reactively.

---

# Summary

| Concept            | Key Idea                            |
| ------------------ | ----------------------------------- |
| Old Error Handling | Weak, ambiguous, no trace           |
| Java Exceptions    | Structured failure handling         |
| `finally`          | Cleanup logic always executed       |
| Runtime Exceptions | Indicate programming mistakes       |
| Best Practice      | Fail clearly, recover intentionally |

> Clean error handling is a core part of professional-grade software.

---

<!-- _class: lead -->

# Thank You!

<div class="cols">
<div>
<p class="pill">Error Handling & Exception Management</p>
</div>
<div class="imgbox">
![width:850](assets/12/exception-thanks.png)
</div>
</div>

**Sharif University of Technology — Advanced Programming — Fall 2025**

