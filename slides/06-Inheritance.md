---
marp: true
theme: default
paginate: true
backgroundColor: #ffffff
color: #000000
header: "![height:25](assets/sharif-logo-blue.png) **Advanced Programming (AP) — Object-Oriented Concepts in Java**"
footer: "**Sharif University of Technology** • Fall 2025 • Mr. Ali Najimi • Hossein Masihi"
style: |
  :root { --brand: #1966ab; --text: #000000; }
  section { background-color: #ffffff; color: var(--text); font-size: 28px; font-family: 'Inter','Segoe UI','Roboto','Helvetica Neue',Arial,sans-serif; }
  h1, h2, h3 { color: var(--brand); font-family: 'Inter','Segoe UI','Roboto','Helvetica Neue',Arial,sans-serif; }
  ul { margin-top: 10px; }
  .cols { display: grid; grid-template-columns: 1.5fr 0.5fr; gap: 28px; align-items: start; }
  .imgbox { border: 1px solid #eee; padding: 8px; border-radius: 10px; text-align:center; }
  .imgbox img { border-radius: 10px; border: 3px solid #1966ab; }
  .pill { display:inline-block; padding: 4px 10px; border:1px solid var(--brand); border-radius:999px; color: var(--brand); font-size:20px; }
  section.lead header, section.lead footer { display: none !important; }

---

<!-- _class: lead -->
![bg right:30% 90%](assets/sharif-logo-blue.png)
# Advanced Programming
## Inheritance & Polymorphism in Java

**Instructor:** Ali Najimi  
**Author:** Hossein Masihi  
**Department of Computer Engineering**  
**Sharif University of Technology**  
**Fall 2025**

---

# Table of Contents

1. Inheritance — Concept  
2. Access Modifiers: protected  
3. Abstract Classes  
4. The `super` Keyword  
5. Multiple Inheritance in Other Languages  
6. Polymorphism — Concept & Usage  
7. Examples and Diagrams  

---

# Inheritance — Concept

<div class="cols">
<div>

* Allows a class (**subclass**) to **reuse** and **extend** another class (**superclass**).  
* Enables **code reuse**, **hierarchical organization**, and **specialization**.  
* Example:  
  - `Animal` → general behavior  
  - `Bird`, `Fish`, `Mammal` → specialized types  

> Inheritance models **"is-a"** relationships.

</div>
<div>
  <div class="imgbox">
  
![width:750](assets/06/inheritance-concept.png)
  </div>
</div>
</div>

---

# Inheritance in Java

```java
class Animal {
    void eat() {
        System.out.println("Animal is eating...");
    }
}
class Dog extends Animal {
    void bark() {
        System.out.println("Dog is barking...");
    }
}
````

```java
Dog d = new Dog();
d.eat();   // Inherited from Animal
d.bark();  // Defined in Dog
```

> `Dog` inherits all accessible methods and properties of `Animal`.

---

# The `protected` Access Modifier

<div class="cols">
<div>

* `protected` members are:

    * accessible **within the same package**
    * accessible **by subclasses**, even in other packages

* Useful for inheritance when you want to **allow extension**, not full exposure.

```java
class Animal {
    protected String name;
}
```

> `protected` = bridge between `private` and `public`.

</div>
<div>
  <div class="imgbox">

![width:750](assets/06/protected.png)

  </div>
</div>
</div>

---

# Abstract Classes

<div class="cols">
<div>

* Define **incomplete behavior** to be **implemented by subclasses**.
* Cannot be instantiated directly.
* May include both **abstract** and **concrete** methods.

```java
abstract class Animal {
    abstract void makeSound();
    void eat() {System.out.println("Eating...");}
    }
```

```java
class Dog extends Animal {
    void makeSound() {System.out.println("Woof!");} 
    }
```

</div>
<div>
  <div class="imgbox">

![width:850](assets/06/abstract.png)

  </div>
</div>
</div>

---

# The `super` Keyword

<div class="cols">
<div>

* Refers to the **immediate parent class**.
* Used to:

    * call **parent constructor**
    * access **parent methods or fields**

```java
class Animal {
    Animal(String name) { System.out.println("Animal: " + name); }
}

class Dog extends Animal {
    Dog(String name) {
        super(name); // calls parent constructor
        System.out.println("Dog created.");
    }
}
```

</div>
<div>
  <div class="imgbox">

![width:800](assets/06/super.png)

  </div>
</div>
</div>

---

# Multiple Inheritance (Other Languages)

<div class="cols">
<div>

* **Java does not support multiple class inheritance** (to avoid ambiguity).
* But interfaces allow multiple inheritance of **behavior**.

```java
interface Runnable { void run();}
interface Eatable { void eat();}
class Human implements Runnable, Eatable {
  public void run() {}
  public void eat() {}
}
```

> C++ and Python support multiple inheritance of classes directly.
> Java avoids **diamond problem** by using interfaces.

</div>
<div>
  <div class="imgbox">

![width:850](assets/06/multi-inheritance.png)

  </div>
</div>
</div>

---

# Polymorphism — Concept

<div class="cols">
<div>

* Means **"many forms"**.
* The same method behaves **differently** based on the object calling it.
* Achieved via **method overriding** and **dynamic binding**.

```java
class Animal {
  void sound() { System.out.println("Some sound"); }  }
class Cat extends Animal {
  void sound() { System.out.println("Meow"); }  }
```

```java
Animal a = new Cat();
a.sound(); // "Meow"
```
</div>
<div>
  <div class="imgbox">

![width:850](assets/06/polymorphism.png)

  </div>
</div>
</div>

> The method executed depends on the **actual type**, not reference type.



---

# Why Use Polymorphism?

| Benefit                 | Description                                    |
| ----------------------- | ---------------------------------------------- |
| **Extensibility**       | New subclasses can work with existing code.    |
| **Code Simplification** | Use parent references for multiple subclasses. |
| **Flexibility**         | Different behaviors under one interface.       |
| **Encapsulation**       | Hides specific implementation details.         |

> Real-world: a `ZooManager` can store a list of `Animal` objects
> and call `makeSound()` without knowing each type.

---

# Example — Polymorphism in Practice

```java
Animal[] animals = { new Dog(), new Cat(), new Bird() };

for (Animal a : animals) {
    a.makeSound();
}
```

Output:

```
Woof!
Meow!
Tweet!
```

> All objects respond differently to the same `makeSound()` call.

---

# Summary

| Concept                  | Key Idea                          |
| ------------------------ | --------------------------------- |
| **Inheritance**          | Reuse and extend existing classes |
| **protected**            | Visible to subclasses             |
| **abstract**             | Base for partial implementation   |
| **super**                | Access parent class               |
| **Multiple inheritance** | Supported via interfaces          |
| **Polymorphism**         | One interface, many behaviors     |

> Together, these principles make Java a **powerful OOP language** for reusable and scalable systems.

---

<!-- _class: lead -->

# Thank You

<div class="cols">
<div> 
<p class="pill">Inheritance & Polymorphism in Java</p>
</div>
<div>
  <div class="imgbox">

![width:800](assets/06/oop-thanks.png)

  </div>
</div>
</div>

*Advanced Programming — Fall 2025 — Sharif University of Technology*
