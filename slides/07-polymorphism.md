---
marp: true
theme: default
paginate: true
backgroundColor: #ffffff
color: #000000
header: "![height:25](https://cdn.shraif.ir/cdn/main/ap/sharif-logo-blue.png) **Advanced Programming (AP) — Object-Oriented Concepts in Java**"
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
![bg right:30% 90%](https://cdn.shraif.ir/cdn/main/ap/sharif-logo-blue.png)
# Advanced Programming
## Polymorphism in Java

**Instructor:** Ali Najimi  
**Author:** Hossein Masihi  
**Department of Computer Engineering**  
**Sharif University of Technology**  
**Fall 2025**

---

# Table of Contents

1. Polymorphism — Concept  
2. Implementing Polymorphism with Inheritance  
3. The `final` Keyword and Restrictions  
4. Code Examples  
5. Summary  

---

# Polymorphism — Concept

<div class="cols">
<div>

* **Polymorphism** means *“many forms.”*  
* Same interface or method name can lead to **different behaviors**.  
* Enables **flexibility** and **extensibility** in OOP.  

Two major types:
1. **Compile-time** (Method Overloading)  
2. **Runtime** (Method Overriding)

> In Java, runtime polymorphism happens via **method overriding**.

</div>
<div>
  <div class="imgbox">

![width:750](assets/07/polymorphism-concept.png)
  </div>
</div>
</div>

---

# Example — Concept

```java
class Animal {
    void sound() {System.out.println("Some generic sound");}
    }
class Dog extends Animal {
    void sound() {System.out.println("Woof");}
}
class Cat extends Animal {
    void sound() {System.out.println("Meow");}
}
```
```java
Animal a1 = new Dog();
Animal a2 = new Cat();
a1.sound();  // Woof
a2.sound();  // Meow
```

> One method call → different outputs depending on the actual object.

---

# How Polymorphism Works with Inheritance

<div class="cols">
<div>

* Inheritance provides the **structure**
  → subclasses inherit and **override** parent methods.
* Polymorphism provides the **behavioral flexibility**
  → method call resolved at **runtime** based on actual type.

```java
Animal a = new Dog();
a.sound(); // Executes Dog’s version
```

> Compiler looks at the reference type,
> JVM calls the **actual object’s** method at runtime.

</div>
<div>
  <div class="imgbox">

![width:800](assets/07/polymorphism-inheritance.png)

  </div>
</div>
</div>

---

# Example — Dynamic Method Dispatch

```java
class Animal {
    void makeSound() { 
      System.out.println("Animal sound"); 
    }
}

class Dog extends Animal {
    void makeSound() { 
      System.out.println("Dog barks"); 
    }
}
class Cat extends Animal {
    void makeSound() { 
      System.out.println("Cat meows"); 
      }
}
```
---

```java

public class Test {
    public static void main(String[] args) {
        Animal a = new Dog();
        a.makeSound(); // "Dog barks"
        a = new Cat();
        a.makeSound(); // "Cat meows"
    }
}
```

> This mechanism is called **Dynamic Method Dispatch**.

---

# The `final` Keyword — Preventing Overrides

<div class="cols">
<div>

* `final` is used to **restrict inheritance or modification**.
* Can be applied to:

    * **Variables:** cannot be reassigned
    * **Methods:** cannot be overridden
    * **Classes:** cannot be subclassed

</div>
<div>
  <div class="imgbox">

![width:850](assets/07/final-keyword.png)

  </div>
</div>
</div>

---

```java
final class Animal { } // No subclass allowed
```
```java
class Dog {
    final void bark() {System.out.println("Bark!");}
}
```

> Marking methods as `final` can improve security and performance.


---

# Example — Final Variable

```java
class Zoo {
    final String name = "Sharif Zoo";

    void display() {
        // name = "Tehran Zoo"; // ❌ Error: cannot assign a value to final variable
        System.out.println(name);
    }
}
```

> `final` variables act like **constants** in Java.

---

# Summary

| Concept             | Description                                 |
| ------------------- | ------------------------------------------- |
| **Polymorphism**    | Many forms; same method, different behavior |
| **Inheritance**     | Enables reuse and specialization            |
| **Dynamic Binding** | Method resolved at runtime                  |
| **final method**    | Prevents overriding                         |
| **final class**     | Prevents inheritance                        |
| **final variable**  | Makes the value constant                    |

> Polymorphism + Inheritance → Core of Java’s flexibility and design extensibility.

---

<!-- _class: lead -->

# Thank You

<div class="cols">
<div> 
<p class="pill">Polymorphism in Java</p>
</div>
<div>
  <div class="imgbox">

![width:800](assets/07/polymorphism-thanks.png)

  </div>
</div>
</div>

*Advanced Programming — Fall 2025 — Sharif University of Technology*