---

marp: true
theme: default
class: lead
paginate: true
backgroundColor: #ffffff
color: #000000
style: |
section {
background-color: #ffffff;
color: #000000;
}
h1, h2, h3 {
color: #1966ab;
}
-
---
# Advanced Programming
## Object-Oriented Programming (OOP) Introduction

**Teacher:** Dr. Ali Najimi
**Writer:** Hossein Masihi
**Sharif University of Technology**
**Fall 2025**

---

## History of Programming Paradigms

* Evolution of programming:

  1. Machine Programming → Binary instructions.
  2. Assembly Programming → Low-level symbolic language.
  3. Structured Programming → Use of loops, functions, modules.
  4. Procedural Programming → Organized code using functions.
  5. Object-Oriented Programming → Encapsulation of data and behavior.
* Each paradigm solved problems of complexity and scalability.

**Image Suggestion:** Timeline showing evolution: Machine → Assembly → C → C++ → Java.

---

## Machine and Assembly Programming

* **Machine code:** executed directly by CPU, extremely difficult to read.
* **Assembly language:** uses mnemonics instead of binary.

  ```assembly
  MOV AX, 5
  ADD AX, 3
  ```
* Problems:

  * Hardware-dependent.
  * Hard to debug and maintain.
  * Poor readability.

**Image Suggestion:** Screenshot of assembly instructions and binary mapping.

---

## Structured Programming

* Introduced **control structures**: `if`, `for`, `while`.
* Encouraged modularization using **functions**.
* Reduced GOTO-based spaghetti code.
* Example in C:

  ```c
  for(int i = 0; i < 5; i++) {
      printf("%d", i);
  }
  ```
* Problem: hard to manage complex relationships between data and functions.

**Image Suggestion:** Diagram showing structured flow of control.

---

## Procedural Programming

* Focuses on **procedures/functions** as the main building block.
* Code divided into procedures that operate on data.
* Example:

  ```c
  void deposit(float amount) { balance += amount; }
  ```
* Limitations:

  * Data and methods are separate.
  * Difficult to manage large projects.

**Image Suggestion:** Contrast diagram: data vs procedures.

---

## Object-Oriented Programming (OOP)

* Introduced in **Simula (1967)**, popularized by **C++** and **Java**.
* Models software after real-world entities.
* Combines **data (attributes)** and **functions (methods)** into one unit — the **object**.
* Promotes **reuse**, **maintainability**, and **scalability**.

**Image Suggestion:** Diagram showing object encapsulating data and methods.

---

## Objects

* An **object** represents a real-world entity.

  * Example: `Student`, `Car`, `Book`.
* It contains:

  * **Attributes:** represent state/data.
  * **Methods:** represent behaviors.
* Example:

  ```java
  class Car {
      int speed;
      void drive() { System.out.println("Driving..."); }
  }
  ```

**Image Suggestion:** UML diagram showing Car class → attributes/methods.

---

## Properties (Attributes) and Procedures (Methods)

* **Attributes:** variables inside a class.
* **Methods:** actions or behaviors of objects.
* Together they define how an object behaves.
* Example:

  ```java
  class Student {
      String name;
      void study() {
          System.out.println(name + " is studying");
      }
  }
  ```

**Image Suggestion:** Object diagram: Student object with properties and actions.

---

## Classes

* A **class** is a **blueprint** for creating objects.
* Defines structure and behavior.
* Example:

  ```java
  class Circle {
      double radius;
      double area() {
          return Math.PI * radius * radius;
      }
  }
  ```
* Object creation:

  ```java
  Circle c1 = new Circle();
  c1.radius = 5;
  System.out.println(c1.area());
  ```

**Image Suggestion:** Blueprint analogy: Class as design → Object as instance.

---

## Principles of OOP

* **Encapsulation:** binding data & methods together.
* **Inheritance:** one class derives properties from another.
* **Polymorphism:** one interface, multiple implementations.
* **Abstraction:** hiding internal complexity.

**Image Suggestion:** Infographic of 4 OOP pillars.

---

## Advantages of OOP

* Code reuse (inheritance).
* Easier debugging and testing.
* Better organization for large projects.
* Encourages modular and team-based development.

**Image Suggestion:** Comparison chart: Procedural vs Object-Oriented.

---

# Thank You 🙌

**Good luck and happy coding!**
*Advanced Programming – Fall 2025 – Sharif University of Technology*
