---
marp: true
theme: default
paginate: true
backgroundColor: #ffffff
color: #000000
header: "![height:25](https://cdn.shraif.ir/cdn/main/ap/sharif-logo-blue.png) **Advanced Programming (AP) — Software Testing**"
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
## Software Testing — Foundations, Tools, Practices

**Instructor:** Ali Najimi  
**Author:** Hossein Masihi  
Sharif University of Technology — Fall 2025

---

# Table of Contents

1. What is Software Testing?  
2. QA vs Testing  
3. Unit Testing  
4. JUnit Framework  
5. Throwing & Handling Exceptions  
6. Mocking Dependencies  
7. Summary

---

# What is Software Testing?

* Software Testing is the process of **verifying and validating** that a software system:
  - Works correctly
  - Meets requirements
  - Handles errors gracefully
  - Maintains quality over time

> Testing is not optional — it is essential for reliability & maintainability.

---

# QA vs Testing

| Aspect | QA (Quality Assurance) | Testing |
|-------|------------------------|---------|
| Focus | Process & standards | Software behavior |
| Goal | Prevent defects | Find defects |
| Activities | Reviews, guidelines, documentation | Executing test cases |
| Responsibility | Whole team | Testers + Developers |

> QA = Prevention  
> Testing = Detection

---

# Unit Testing

* Tests **smallest functional units** (methods/classes)
* Must be:
  - **Fast**
  - **Repeatable**
  - **Independent**
* Written and maintained by **developers**

```java
int add(int a, int b) { return a + b; }
````

Unit test verifies:

```java
assertEquals(5, add(2, 3));
```

> Unit Tests prove code correctness in isolation.

---

# JUnit — Standard Java Testing Framework

```java
import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.*;

class CalculatorTest {

    @Test
    void testAdd() {
        Calculator c = new Calculator();
        assertEquals(7, c.add(3, 4));
    }
}
```

* **@Test** marks a test method
* **assertEquals** checks expected vs actual values

> JUnit is the core testing tool in Java environments.

---

# Throwing and Testing Exceptions

```java
class BankAccount {
    private double balance = 0;

    public void withdraw(double amount) {
        if (amount > balance)
            throw new IllegalArgumentException("Insufficient funds");
        balance -= amount;
    }
}
```

Testing the thrown exception:

```java
@Test
void testWithdrawException() {
    BankAccount b = new BankAccount();
    assertThrows(IllegalArgumentException.class, () -> b.withdraw(100));
}
```

> Exception testing ensures **safe failure behavior**.

---

# Mocking Dependencies

Used when:

* The class you're testing depends on something **external**:

    * Database
    * Network
    * File system
    * API service

We **replace real dependencies** with **mocks**.

```java
@Mock EmailService email;
@InjectMocks UserManager manager;
```

> Mocking isolates **logic** from external systems → reliable tests.

---

<div class="imgbox">

![width:750](assets/09/mocking-diagram.png)

</div>

> Real world systems rely heavily on mocking frameworks like Mockito.

---

# Summary

| Concept    | Description                      |
| ---------- | -------------------------------- |
| QA         | Process of maintaining quality   |
| Unit Test  | Tests the smallest components    |
| JUnit      | The standard Java test framework |
| Exceptions | Must be tested, not ignored      |
| Mocking    | Isolates code from dependencies  |

> Consistent testing → Software that is stable, trustworthy, and maintainable.

---

<!-- _class: lead -->

# Thank You!

<div class="cols">
<div>
<p class="pill">Software Testing — Core Foundations</p>
</div>
<div class="imgbox">

![width:850](assets/09/testing-thanks.png)

</div>
</div>

**Sharif University of Technology — Advanced Programming — Fall 2025**

