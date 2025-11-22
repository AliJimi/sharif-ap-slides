---
marp: true
theme: default
paginate: true
backgroundColor: #ffffff
color: #000000
header: "![height:25](https://cdn.shraif.ir/cdn/main/ap/sharif-logo-blue.png) **Advanced Programming (AP) — Refactoring**"
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
## Refactoring — Improving Code Quality

**Instructor:** Ali Najimi  
**Author:** Hossein Masihi
**Department of Computer Engineering**  
**Sharif University of Technology**  
**Fall 2025**

---

# Table of Contents

1. Refactoring — Concept  
2. Clean Code Principles  
3. Recognizing Bad Code Smells  
4. Refactoring Techniques (Patterns)  
5. Example  
6. Summary


---

  <div class="imgbox">

  ![width:950](assets/11/refactoring-concept.png)
  </div>

---

# Refactoring — Concept

<div class="cols">
<div>

* **Refactoring** is the process of **improving internal code structure**  
  *without changing external behavior*.
* Goal:
  - Cleaner structure
  - Better readability
  - Easier maintenance
  - Fewer bugs over time

> "Refactoring is improving the design after the code is written." — Martin Fowler

</div>
<div>
  <div class="imgbox">

  ![width:850](assets/11/refactor.png)
  </div>
</div>
</div>

---

# Clean Code Principles

<div class="cols">
<div>

| Principle | Meaning |
|---------|---------|
| Readability | Code should be easy to understand |
| Single Responsibility | Each unit has one purpose |
| Small Functions | Functions should do *one thing* |
| Naming Matters | Clear, intention-revealing names |
| No Duplication | Reuse logic instead of copy-paste |

> Code is read **more often** than it is written.

</div>
<div>
  <div class="imgbox">

  ![width:850](assets/11/big-refactoring-meme.png)
  </div>
</div>
</div>
---

# Bad Code — Code Smells

| Smell | Description |
|------|-------------|
| Long Method | Too much logic in one function |
| Large Class | Too many responsibilities |
| Magic Numbers | Unclear hardcoded values |
| Duplicated Code | Same logic in multiple places |
| Feature Envy | One class uses another class’s data excessively |

> Code smells indicate **where** refactoring is needed.

---

# Example of Bad Code (Before Refactoring)

```java
double calculateTotal(double price, double tax) {
    double t = price * tax;
    System.out.println("Total: " + (price + t));
    return price + t;
}
````

Problems:

* Mixed **calculation** and **printing**
* Ambiguous variable naming

---


  <div class="imgbox">

  ![width:950](assets/11/refactoring_time.png)
  </div>

---
# After Refactoring

```java
double calculateTotal(double price, double tax) {
    return price + taxAmount(price, tax);
}

double taxAmount(double price, double tax) {
    return price * tax;
}
```

* Clear naming
* Separated responsibilities
* Reusable logic

> Cleaner code → easier testing and extension.

---

# Common Refactoring Patterns

| Pattern                                | Purpose                               |
| -------------------------------------- | ------------------------------------- |
| **Extract Method**                     | Split large methods into smaller ones |
| **Rename Variable**                    | Improve meaning of identifiers        |
| **Extract Class**                      | Move responsibilities into new class  |
| **Inline Method**                      | Remove unnecessary methods            |
| **Replace Magic Number with Constant** | Improve clarity and configurability   |

---

# Refactoring + Testing

* Refactor **only when tests exist**
* Unit tests guarantee behavior stays the same
* Refactoring should **not change output**

> Testing + Refactoring = Safe Continuous Improvement

---

# Summary

| Concept              | Key Idea                                             |
| -------------------- | ---------------------------------------------------- |
| Refactoring          | Improve internal structure without changing behavior |
| Clean Code           | Readable, simple, intention-revealing                |
| Code Smells          | Signals for needed improvement                       |
| Refactoring Patterns | Systematic ways to improve design                    |

> Great developers continually refactor — not just write code.

---

<!-- _class: lead -->

# Thank You!

<div class="cols">
<div>


<p class="pill">Refactoring — Clean Code for the Future</p>
</div>
<div class="imgbox">

![width:850](assets/11/no_more_refactor.png)
</div>
</div>

**Sharif University of Technology — Advanced Programming — Fall 2025**


