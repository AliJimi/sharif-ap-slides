---
marp: true
theme: default
paginate: true
backgroundColor: #ffffff
color: #000000
header: "![height:25](https://cdn.shraif.ir/cdn/main/ap/sharif-logo-blue.png) **Advanced Programming (AP) — File & Stream I/O**"
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
## File, Stream & Serialization in Java

**Instructor:** Ali Najimi  
**Author:** Hossein Masihi  
Sharif University of Technology — Fall 2025

---

# Table of Contents

1. What Are Streams?  
2. Input & Output in Java  
3. Reading & Writing Files  
4. Byte Streams vs Character Streams  
5. Serialization  
6. Summary

---

# Streams — Concept

<div class="cols">
<div>

* A **stream** is a flow of data.
* Java I/O works through **streams**:
  - InputStream → read data
  - OutputStream → write data
* Streams are **sequential** data channels.

> Everything in Java I/O is built around streams.

</div>
<div>
  <div class="imgbox">

  ![](assets/15/io-outs.gif)
  </div>
</div>
</div>

---

  <div class="imgbox">

  ![](assets/15/file_streams.png)
  </div>

---

# Input & Output Overview

| Type | Parent Class | Purpose |
|------|--------------|---------|
| **Byte Stream** | `InputStream`, `OutputStream` | Handles raw binary data |
| **Character Stream** | `Reader`, `Writer` | Handles text characters with encoding |

```java
InputStream in = new FileInputStream("data.bin");
Reader reader = new FileReader("data.txt");
````

---

# Reading a File (Character Stream)

```java
try (BufferedReader br = new BufferedReader(new FileReader("input.txt"))) {
    String line;
    while ((line = br.readLine()) != null) {
        System.out.println(line);
    }
}
```

* `BufferedReader` improves efficiency
* `try-with-resources` auto-closes the file

---

# Writing to a File

```java
try (BufferedWriter bw = new BufferedWriter(new FileWriter("output.txt"))) {
    bw.write("Sharif University");
}
```

* Writing happens in **text form**
* Buffered writers reduce disk operations

---

# Byte Streams — Handling Raw Data

```java
try (FileInputStream in = new FileInputStream("image.png");
     FileOutputStream out = new FileOutputStream("copy.png")) {

    int data;
    while ((data = in.read()) != -1) {
        out.write(data);
    }
}
```

> Used for images, audio, compiled files, etc.


---

  <div class="imgbox">

  ![](assets/15/byte_streams.png)
  </div>

---

# Serialization — Storing Objects

* Serialization converts an **object into a byte stream**
* Allows:

    * Saving objects to disk
    * Sending objects over network

```java
class Student implements Serializable {
    String name;
    int id;
}
```

---

# Writing Serialized Objects

```java
ObjectOutputStream out = new ObjectOutputStream(new FileOutputStream("std.bin"));
out.writeObject(new Student("Ali", 401110891));
out.close();
```

# Reading Serialized Objects

```java
ObjectInputStream in = new ObjectInputStream(new FileInputStream("std.bin"));
Student s = (Student) in.readObject();
in.close();
```

> Requires class to implement `Serializable`.

---

# Summary

| Concept          | Description                                    |
| ---------------- | ---------------------------------------------- |
| Stream           | Sequential data flow                           |
| Byte Stream      | Raw data (binary)                              |
| Character Stream | Encoded text                                   |
| File I/O         | Reading and writing text and binary files      |
| Serialization    | Converting objects → transferable byte streams |

> Mastering I/O is essential for data processing applications.

---

<!-- _class: lead -->

# Thank You!

<div class="cols">
<div>
<p class="pill">Java File & Stream — Practical I/O</p>
</div>
<div class="imgbox">

![width:850](assets/15/stream-thanks.png)
</div>
</div>

**Sharif University of Technology — Advanced Programming — Fall 2025**
