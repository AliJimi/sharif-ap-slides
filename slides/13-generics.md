---
marp: true
theme: default
paginate: true
backgroundColor: #ffffff
color: #000000
header: "![height:25](https://cdn.shraif.ir/cdn/main/ap/sharif-logo-blue.png) **Advanced Programming (AP) — Generics in Java**"
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
  .cols { display: grid; grid-template-columns: 1.2fr 0.8fr; gap: 24px; align-items: start; }
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
## Generics in Java — Type Safety & Reusability

**Instructor:** Ali Najimi  
**Author:** Hossein Masihi
**Department of Computer Engineering**  
**Sharif University of Technology**  
**Fall 2025**

---

# Table of Contents

1. What Are Generics?  
2. Generic Classes  
3. Generic Methods  
4. Creating Generic Objects  
5. Generics in Inheritance  
6. Summary  

---

# Generics — Concept

<div class="cols">
<div>

* Generics provide **type safety** and **reuse** in class and method definitions.
* They allow defining classes, interfaces, and methods **without specifying exact data types**.
* Prevents runtime errors like `ClassCastException`.

> Generics enable **compile-time type checking**.

</div>
<div>
  <div class="imgbox">

  ![width:850](assets/13/generics-concept.png)
  </div>
</div>
</div>

---

# Generic Class Example

```java
class Box<T> {
    private T value;

    public void set(T value) { this.value = value; }
    public T get() { return value; }
}
````

```java
Box<Integer> intBox = new Box<>();
intBox.set(42);

Box<String> strBox = new Box<>();
strBox.set("Sharif");
```

> `T` is a type placeholder. Replaced when object is created.

---

# Generic Method Example

```java
class Utils {
    public static <T> void print(T item) {
        System.out.println(item);
    }
}
```

```java
Utils.print(100);
Utils.print("Sharif");
Utils.print(3.14);
```

> Generic methods define their own type parameter.

---

# Creating Generic Objects

Without Generics (Old Java):

```java
List list = new ArrayList();
list.add("Hello");
list.add(10); // no type safety
```

With Generics:

```java
List<String> list = new ArrayList<>();
list.add("Hello");
// list.add(10); // compile-time error
```

> Generics **prevent invalid types** from being inserted.

---

# Generics in Inheritance

* **Generics are not covariant** by default.

```java
List<Object> a;
List<String> b;

// a = b; // Not allowed
```

But:

```java
List<? extends Number> nums;
nums = new ArrayList<Integer>(); // OK
nums = new ArrayList<Double>();  // OK
```

> Use **wildcards (`? extends`, `? super`)** to allow controlled flexibility.

---

# Bounded Type Parameters

```java
class Calculator<T extends Number> {
    double square(T n) {
        return n.doubleValue() * n.doubleValue();
    }
}
```

```java
Calculator<Integer> c1 = new Calculator<>();
Calculator<Double> c2 = new Calculator<>();
```

> Restricts generic types to specific inheritance hierarchies.

---

# Summary

| Concept        | Description                                   |
| -------------- | --------------------------------------------- |
| Generics       | Enable type-safe reusable classes and methods |
| Generic Class  | Uses type placeholders (e.g., `class Box<T>`) |
| Generic Method | Defines `<T>` before return type              |
| Wildcards      | Allow controlled flexibility in inheritance   |
| Benefit        | Eliminates runtime casting errors             |

> Generics make code **safer, cleaner, and more reusable**.

---

<!-- _class: lead -->

# Thank You!

<div class="cols">
<div>
<p class="pill">Generics in Java — Safe and Flexible Abstraction</p>
</div>
<div class="imgbox">

![width:850](assets/13/generics-thanks.png)
</div>
</div>

**Sharif University of Technology — Advanced Programming — Fall 2025**
