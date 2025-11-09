---
marp: true
theme: default
paginate: true
backgroundColor: #ffffff
color: #000000
header: "![height:25](https://cdn.shraif.ir/cdn/main/ap/sharif-logo-blue.png) **Advanced Programming (AP) — Advanced Java**"
footer: "**Sharif University of Technology** • Fall 2025 • Mr. Ali Najimi • Hossein Masihi"
style: |
  :root { --brand:#1966ab; --text:#000000; }
  section {
    background-color:#ffffff;
    color:var(--text);
    font-size:28px;
    font-family:'Inter','Segoe UI','Roboto','Helvetica Neue',Arial,sans-serif;
    animation:fadeIn .9s ease-in;
  }
  h1,h2,h3 { color:var(--brand); animation:slideUp .8s ease-out; }
  ul,p,pre,table { animation:fadeIn 1s ease-in; }
  code { font-size:90%; }
  .cols { display:grid;grid-template-columns:1.4fr 0.6fr;gap:24px;align-items:start; }
  .imgbox { border:1px solid #eee;padding:8px;border-radius:10px;text-align:center;animation:zoomIn 1s ease-in; }
  .imgbox img { border-radius:10px;border:3px solid #1966ab; }
  @keyframes fadeIn { from{opacity:0;transform:translateY(10px);} to{opacity:1;transform:translateY(0);} }
  @keyframes slideUp { from{opacity:0;transform:translateY(20px);} to{opacity:1;transform:translateY(0);} }
  @keyframes zoomIn { from{opacity:0;transform:scale(0.9);} to{opacity:1;transform:scale(1);} }
---

<!-- _class: lead -->
![bg right:30% 90%](https://cdn.shraif.ir/cdn/main/ap/sharif-logo-blue.png)
# Advanced Java
## Inner Classes, Anonymous Classes, Annotations, Enumerations

**Instructor:** Ali Najimi  
**Author:** Hossein Masihi  
Sharif University of Technology — Fall 2025

---

# Inner Class — Concept

* An **inner class** is a class defined **inside another class**.
* Used when a class is meaningful only inside its enclosing class.

```java
class Outer {
    private int x = 10;

    class Inner {
        void show() { System.out.println(x); }
    }
}
````

Usage:

```java
Outer.Inner obj = new Outer().new Inner();
obj.show();
```

> Inner classes increase encapsulation and logical grouping.

---

# Inner Classes — Where Errors Occur

| Issue                       | Cause                                               |
| --------------------------- | --------------------------------------------------- |
| `OuterClass.this` confusion | Accessing outer fields incorrectly                  |
| Memory leaks                | Inner class holding reference to outer instance     |
| `static` inner rules        | Non-static inner classes cannot have static members |

---

# Anonymous Class — Concept

* An **anonymous class** is a class with **no name**, created for **one-time use**.
* Often used with **interfaces or abstract classes**.

```java
Runnable r = new Runnable() {
    public void run() {
        System.out.println("Running anonymously");
    }
};
new Thread(r).start();
```

> Useful when implementation is used **once** and does not deserve a named class.

---

# Anonymous Class — Common Misuses

| Problem                          | Description                  |
| -------------------------------- | ---------------------------- |
| Hard to read                     | No class name → less clarity |
| Hard to test                     | No reusable type             |
| Should not contain complex logic | Becomes anti-clean-code      |

---

# Annotations — Concept

* **Annotations** provide metadata to compiler or runtime.
* They **do not directly execute**, but tools use their information.

Examples:

```java
@Override
@SuppressWarnings("unchecked")
```

Custom Annotation:

```java
@interface Info {
    String author();
    int version();
}
```

Usage:

```java
@Info(author="Hossein", version=1)
class Example {}
```

---

# Annotation Processing & Errors

| Error                             | Cause                                            |
| --------------------------------- | ------------------------------------------------ |
| `AnnotationTypeMismatchException` | Wrong annotation value type                      |
| Annotation ignored                | Tool/framework not configured to process it      |
| Retention issues                  | `@Retention` set incorrectly (SOURCE vs RUNTIME) |

---

# Enumeration (enum) — Concept

* **enum** is a type that represents a **fixed set of constants**.

```java
enum Day { MON, TUE, WED, THU, FRI, SAT, SUN }
```

Usage:

```java
Day d = Day.MON;
```

Enums can also have methods:

```java
enum Status {
    SUCCESS(200), ERROR(500);
    int code;
    Status(int c){ code = c; }
}
```

---

# Enumeration — When Errors Happen

| Error                                    | Cause                                        |
| ---------------------------------------- | -------------------------------------------- |
| `IllegalArgumentException`               | Calling `Enum.valueOf()` with invalid string |
| Switch-case missing default              | Can lead to unhandled states                 |
| Mixing string constants instead of enums | Lose type safety                             |

```java
Status s = Status.valueOf("FAIL"); // IllegalArgumentException
```

---

# Summary

| Topic           | Key Point                                   |
| --------------- | ------------------------------------------- |
| Inner Class     | Defined inside another class to group logic |
| Anonymous Class | Temporary one-time class implementation     |
| Annotation      | Metadata for compiler/runtime tools         |
| Enumeration     | Defines a fixed set of constant values      |

> These advanced features enable cleaner structure, metadata usage, and safer constant values.

---

<!-- _class: lead -->

# Thank You!

**Sharif University of Technology — Advanced Programming — Fall 2025**
