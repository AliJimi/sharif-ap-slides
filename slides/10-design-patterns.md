---
marp: true
theme: default
paginate: true
backgroundColor: #ffffff
color: #000000
header: "![height:25](https://cdn.shraif.ir/cdn/main/ap/sharif-logo-blue.png) **Advanced Programming (AP) — Design Patterns**"
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
## Design Patterns — Concepts and GoF Patterns

**Instructor:** Ali Najimi  
**Author:** Hossein Masihi  
Sharif University of Technology — Fall 2025

---

# Table of Contents

1. What Are Design Patterns?  
2. Why Patterns Matter  
3. Gang of Four (GoF) Pattern Categories  
4. Examples  
5. Other Modern Patterns  
6. Summary

---

# Design Patterns — Concept

<div class="cols">
<div>

* **Design Patterns** are **reusable solutions** to common software design problems.
* They provide:
  - Shared vocabulary
  - Proven architecture approaches
  - Maintainable and scalable design strategy

> Patterns do not give code — they guide structure and behavior.

</div>
<div>
  <div class="imgbox">

  ![width:850](assets/10/design-patterns-concept.png)

  </div>
</div>
</div>

---

# Why Use Design Patterns?

| Benefit | Explanation |
|--------|-------------|
| Reusability | Solutions can apply across projects |
| Maintainability | Clear structure reduces complexity |
| Communication | Common terminology improves teamwork |
| Quality | Prevents reinventing poor solutions |

> Patterns make design intentional — not accidental.

---

# The Gang of Four (GoF) Patterns

* Introduced in the book:  
  **“Design Patterns: Elements of Reusable Object-Oriented Software” (1994)**

Categorized into **3 groups**:

| Category | Purpose |
|---------|---------|
| **Creational** | Object creation management |
| **Structural** | Class and object composition |
| **Behavioral** | Object interaction and responsibility |

---

# Creational Patterns (Examples)

| Pattern | Purpose |
|--------|---------|
| **Singleton** | Only one instance exists globally |
| **Factory Method** | Delegates object creation to subclasses |
| **Builder** | Constructs complex objects step-by-step |

Example — Singleton:

```java
class Database {
    private static Database instance = new Database();
    private Database() {}
    public static Database getInstance() { return instance; }
}
````

---

# Structural Patterns (Examples)

| Pattern       | Purpose                                        |
| ------------- | ---------------------------------------------- |
| **Adapter**   | Convert one interface to another               |
| **Decorator** | Add behavior dynamically                       |
| **Facade**    | Provide a simple interface to a complex system |

Example — Adapter:

```java
interface USBC { void connect(); }
class HDMI {   void plugHDMI() { System.out.println("HDMI connected"); }  }
class HDMItoUSBAdapter implements USBC {
    private HDMI hdmi = new HDMI();
    public void connect() { hdmi.plugHDMI(); }
}
```

---

# Behavioral Patterns (Examples)

| Pattern      | Purpose                            |
| ------------ | ---------------------------------- |
| **Strategy** | Select algorithm at runtime        |
| **Observer** | Notify dependents automatically    |
| **Command**  | Encapsulate a request as an object |

Example — Strategy:

```java
interface SortStrategy { void sort(int[] data); }
class QuickSort implements SortStrategy {   public void sort(int[] data) { /* ... */ }  }
class SortContext {
    private SortStrategy strategy;
    SortContext(SortStrategy strategy) { this.strategy = strategy; }
    void execute(int[] data) { strategy.sort(data); }
}
```

---

# Other Useful Patterns (Beyond GoF)

| Pattern                       | Domain                           |
| ----------------------------- | -------------------------------- |
| **MVC / MVVM**                | UI architecture                  |
| **Repository**                | Data layer abstraction           |
| **Dependency Injection**      | Manage object dependencies       |
| **Event-Driven Architecture** | Distributed system communication |

> Modern software combines GoF patterns with architectural patterns.

---

# Summary

| Concept         | Description                                    |
| --------------- | ---------------------------------------------- |
| Design Patterns | Reusable solutions to common design issues     |
| GoF Categories  | Creational, Structural, Behavioral             |
| Value           | Improves maintainability, quality, and clarity |
| Modern Patterns | Apply at architectural system scale            |

> Good engineers **recognize**, **adapt**, and **apply** patterns.

---

<!-- _class: lead -->

# Thank You!

<div class="">
<div>
<p class="pill">Design Patterns — Core Understanding</p>
</div>
<div class="imgbox">

![width:750](assets/10/design-patterns-thanks.png)
</div>
</div>

**Sharif University of Technology — Advanced Programming — Fall 2025**

