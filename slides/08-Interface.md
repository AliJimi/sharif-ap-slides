---
marp: true
theme: default
paginate: true
backgroundColor: #ffffff
color: #000000
header: "![height:25](https://cdn.shraif.ir/cdn/main/ap/sharif-logo-blue.png) **Advanced Programming (AP) — Interfaces in Java**"
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
## Interfaces in Java — Extended Edition

**Instructor:** Ali Najimi  
**Author:** Hossein Masihi  
**Department of Computer Engineering**  
**Sharif University of Technology**  
**Fall 2025**

---

# Table of Contents

1. Interface — Concept  
2. Purpose and Benefits  
3. Declaring and Implementing Interfaces  
4. Default and Static Methods  
5. Interface vs Abstract Class  
6. Multiple Interface Implementation  
7. Real-World Example  
8. Summary and Key Takeaways

---

<div class="imgbox">

![width:700](assets/08/interface-concept.png)
</div>

---

# Interface — Concept

<div class="cols">
<div>

* An **interface** defines a set of **method signatures**
* Specifies *what* a class must do — not *how*
* Classes **implement** interfaces
* Enables **polymorphism** through behavior contracts

> Interfaces represent **capabilities**, not structures

</div>
<div>
  <div class="imgbox">

  ![width:850](assets/08/interface-structure.png)
  </div>
</div>
</div>

---

# Declaring and Implementing an Interface

```java
interface Shape {
    double area();
    double perimeter();
}
````

```java
class Circle implements Shape {
    private double r;

    Circle(double r) { this.r = r; }

    public double area() { return Math.PI * r * r; }
    public double perimeter() { return 2 * Math.PI * r; }
}
```

> A class must implement **all** interface methods

---

# Why Use Interfaces?

| Benefit              | Description                               |
| -------------------- | ----------------------------------------- |
| Abstraction          | Hide implementation details               |
| Loose Coupling       | Reduces dependency between components     |
| Extensibility        | Easy replacement of behavior              |
| Polymorphism         | Enables behavior switching at runtime     |
| Framework Foundation | Core principle behind Spring / Jakarta EE |

---

# Default and Static Methods (Java 8+)

```java
interface Logger {
    void log(String message);
    default void info(String message) {
        log("INFO: " + message);
    }
    static void help() {System.out.println("Logger usage help");}
}
```

```java
class ConsoleLogger implements Logger {
    public void log(String message) { System.out.println(message); }
}
```

> `default` = shared behavior
> `static` = utility function at interface level

---

# Interface vs Abstract Class

| Feature               | Interface            | Abstract Class               |
| --------------------- | -------------------- | ---------------------------- |
| State (Fields)        | Only constants       | Can have instance variables  |
| Method Implementation | Only default allowed | Can contain method bodies    |
| Constructors          | Not allowed          | Allowed                      |
| Multiple Inheritance  | Allowed              | Not allowed                  |
| Best Usage            | Behavior contract    | Base implementation template |

---

# Multiple Interface Implementation

```java
interface Flyable { void fly(); }
interface Swimmable { void swim(); }

class Duck implements Flyable, Swimmable {
    public void fly() { System.out.println("Duck flying"); }
    public void swim() { System.out.println("Duck swimming"); }
}
```

> Enables **multi-capability classes**

---

# Real-World Example — Payment

```java
interface PaymentMethod {
    void pay(double amount);
}
class CreditCard implements PaymentMethod {
    public void pay(double amount) { System.out.println("Paid via Credit Card"); }
}
class PayPal implements PaymentMethod {
    public void pay(double amount) { System.out.println("Paid via PayPal"); }
}
class Checkout {
    static void process(PaymentMethod method) {
        method.pay(200);
    }
}
```

> System depends on interface → implementations are interchangeable

---

# Summary

| Concept             | Description                                 |
| ------------------- | ------------------------------------------- |
| Interface           | Behavioral contract (what to do)            |
| Implementation      | Provided by classes (how to do it)          |
| Default Methods     | Shared optional behavior                    |
| Multiple Interfaces | Enables multiple capabilities               |
| Goal                | Flexibility, extensibility, maintainability |

> Interfaces are critical for clean, scalable OOP design

---

<!-- _class: lead -->

# Thank You!

<div >
<div>
<p class="pill">Interfaces in Java — Extended</p>
</div>
<div class="imgbox">

![width:450](assets/08/interface-thanks.png)
</div>
</div>

*Advanced Programming — Fall 2025 — Sharif University of Technology*
