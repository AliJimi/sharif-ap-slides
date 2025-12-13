---
marp: true
theme: default
paginate: true
backgroundColor: #ffffff
color: #000000
header: "![height:25](https://cdn.shraif.ir/cdn/main/ap/sharif-logo-blue.png) **Advanced Programming (AP) — Java Containers & Data Structures**"
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
  .cols { display: grid; grid-template-columns: 1.1fr 0.9fr; gap: 24px; align-items: start; }
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
## Containers — Java Data Structures

**Instructor:** Ali Najimi  
**Author:** Hossein Masihi  
Sharif University of Technology — Fall 2025

---

# Table of Contents

1. What Are Containers?  
2. Java Collections Framework  
3. Lists  
4. Sets  
5. Maps  
6. Choosing the Right Data Structure  
7. Summary

---

# Containers — Concept

<div class="cols">
<div>

* A **container** is a data structure that stores and organizes objects.
* Java provides the **Collections Framework**, offering reusable data structures.
* Key Concepts:
  - Storage
  - Access rules
  - Performance characteristics

> Containers impact time complexity, memory use, and app performance.

</div>
<div>
  <div class="imgbox">

  ![width:850](assets/14/containers-concept.png)
  </div>
</div>
</div>

---

# Java Collections Framework Overview

| Interface | Implementations | Key Feature |
|----------|----------------|-------------|
| **List** | ArrayList, LinkedList | Ordered, allows duplicates |
| **Set** | HashSet, TreeSet | No duplicates |
| **Map** | HashMap, TreeMap | Key-value storage |
| **Queue** | PriorityQueue, ArrayDeque | FIFO ordering |

---

# List — Ordered Collection

```java
List<String> names = new ArrayList<>();
names.add("Ali");
names.add("Hossein");
names.add("Ali"); // duplicates allowed
````

Characteristics:

* Maintains **insertion order**
* Allows **indexed access**
* Allows **duplicate elements**

Use when:

* You need **order** and **random access**

---

# Set — Unique Collection

```java
Set<String> ids = new HashSet<>();
ids.add("A1");
ids.add("A1"); // ignored
ids.add("B3");
```

Characteristics:

* **No duplicates**
* No guaranteed order (unless using TreeSet)
* Efficient membership testing

Use when:

* You care about **uniqueness** of stored items

---

# Map — Key-Value Structure

```java
Map<String, Integer> age = new HashMap<>();
age.put("Ali", 21);
age.put("Sara", 20);
age.put("Ali", 25); // overwrites value
```

Characteristics:

* Fast lookup by **key**
* Keys are unique
* Values may repeat

Use when:

* You need **associative lookup** (dictionary behavior)

---

# Choosing the Right Container

| Requirement            | Best Choice  |
| ---------------------- | ------------ |
| Fast Random Access     | `ArrayList`  |
| Frequent Insert/Delete | `LinkedList` |
| Unique Elements        | `HashSet`    |
| Sorted Elements        | `TreeSet`    |
| Key-Value Lookup       | `HashMap`    |
| Sorted Key-Value       | `TreeMap`    |

> The right container reduces complexity dramatically.

---

# Example Comparison

```java
List<Integer> list = new ArrayList<>();
Set<Integer> set = new HashSet<>();
Map<String, Integer> map = new HashMap<>();
```

| Feature            | List | Set | Map |
| ------------------ | ---- | --- | --- |
| Stores duplicates  | Yes  | No  | N/A |
| Indexed access     | Yes  | No  | No  |
| Key-value behavior | No   | No  | Yes |

---

# Summary

| Concept    | Description                                |
| ---------- | ------------------------------------------ |
| Containers | Structures for storing and organizing data |
| Lists      | Ordered, allow duplicates                  |
| Sets       | Unique elements only                       |
| Maps       | Key-value associations                     |
| Choosing   | Depends on behavior and performance needs  |

> Strong programming requires **choosing the right data structure**.

---

<!-- _class: lead -->

# Thank You!

<div class="cols">
<div>
<p class="pill">Java Data Structures — Core Containers</p>
</div>
<div class="imgbox">

![width:850](assets/14/containers-thanks.png)
</div>
</div>

**Sharif University of Technology — Advanced Programming — Fall 2025**
