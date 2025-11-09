---
marp: true
theme: default
paginate: true
backgroundColor: #ffffff
color: #000000
header: "![height:25](https://cdn.shraif.ir/cdn/main/ap/sharif-logo-blue.png)  Exception & Error Handling — Review"
footer: "Sharif University • Fall 2025 • Instructor: Ali Najimi • Author: Hossein Masihi"
style: |
  :root { --brand:#1966ab; }
  section { font-family:'Inter','Segoe UI','Roboto','Helvetica Neue',sans-serif; font-size:28px; animation:fadeIn .8s }
  h1,h2,h3 { color:var(--brand); animation:slideUp .7s }
  @keyframes fadeIn { from{opacity:0;transform:translateY(10px)} to{opacity:1;transform:translateY(0)} }
  @keyframes slideUp { from{opacity:0;transform:translateY(25px)} to{opacity:1;transform:translateY(0)} }
---

# Error Handling — Before Exceptions

Before exceptions, errors were reported using **return codes**.

```java
int divide(int a, int b) {
    if (b == 0) return -1; // error code
    return a / b;
}
````

Problems:

* Ambiguous — the error value may be a valid result
* No stack trace → difficult debugging
* Logic becomes messy and inconsistent

---

# Exception Management in Java

Java introduces structured error control using `try` / `catch`.

```java
try {
    // code that may fail
} catch (Exception e) {
    // how to respond if failure happens
}
```

Benefits:

* Clear separation of **normal flow** vs **error flow**
* Improves debugging via stack trace
* Enables predictable and maintainable error handling

---

# Checked vs Unchecked Exceptions

| Type          | Extends            | Handling Required?      | Examples                                            | When It Happens                        |
| ------------- | ------------------ | ----------------------- | --------------------------------------------------- | -------------------------------------- |
| **Checked**   | `Exception`        | Yes (compiler-enforced) | `IOException`, `SQLException`                       | External resources (File, DB, Network) |
| **Unchecked** | `RuntimeException` | No                      | `NullPointerException`, `IndexOutOfBoundsException` | Programming logic mistakes             |

> Checked = environment failures
> Runtime = developer mistakes

---

# Common Runtime Exceptions (Code Mistakes)

```java
String name = null;
name.length(); // NullPointerException
```

```java
int[] arr = new int[3];
arr[5] = 10; // ArrayIndexOutOfBoundsException
```

```java
Integer.parseInt("Sharif"); // NumberFormatException
```

**Goal:** Fix logic → **do not** catch them silently.

---

# `finally` — Guaranteed Cleanup

```java
try {
    FileReader r = new FileReader("data.txt");
} catch (FileNotFoundException e) {
    System.out.println("File missing");
} finally {
    System.out.println("Cleanup always executes");
}
```

Used for:

* Closing files
* Closing database connections
* Releasing sockets and system resources

---

# Custom Exceptions — Domain Meaning

```java
class AgeException extends Exception {
    AgeException(String msg) { super(msg); }
}

void register(int age) throws AgeException {
    if (age < 18) throw new AgeException("Age must be 18+");
}
```

**Use when:** The error message should express domain rules clearly.

---

# Generics — Reminder

Goal: **Type Safety + Avoid ClassCastException**

```java
List<String> students = new ArrayList<>();
students.add("Ali");
// students.add(10); // Compile-time error 🚫
```

Without generics:

```java
List list = new ArrayList();
list.add("Ali");
Integer x = (Integer) list.get(0); // ClassCastException ❌
```

---

# Where Errors Occur in Containers

| Structure | Behavior                    | Typical Exceptions                    | When It Happens                        |
| --------- | --------------------------- | ------------------------------------- | -------------------------------------- |
| **List**  | Ordered, duplicates allowed | `IndexOutOfBoundsException`           | Access invalid index                   |
| **Set**   | No duplicates               | —                                     | No runtime error but value ignored     |
| **Map**   | Key-value pairs             | `NullPointerException` (in some maps) | When interacting with null keys/values |

Example:

```java
List<Integer> l = new ArrayList<>();
l.get(5); // IndexOutOfBoundsException
```

---

# File & Stream — Key Errors

```java
BufferedReader br = new BufferedReader(new FileReader("input.txt"));
```

Possible exceptions:

| Exception               | Cause               |
| ----------------------- | ------------------- |
| `FileNotFoundException` | File does not exist |
| `IOException`           | Read/Write failure  |

Safe version:

```java
try (BufferedReader br = new BufferedReader(new FileReader("input.txt"))) {
    System.out.println(br.readLine());
}
```

---

# Serialization — Where Errors Happen

```java
class Student implements Serializable {
    String name;
    int id;
}
```

| Exception                  | Cause                                       |
| -------------------------- | ------------------------------------------- |
| `NotSerializableException` | Class forgot to `implements Serializable`   |
| `InvalidClassException`    | Class structure changed after serialization |

---

# Networking / Sockets — Error Scenarios

```java
Socket socket = new Socket("localhost", 5000);
```

| Exception                | Meaning                     |
| ------------------------ | --------------------------- |
| `ConnectException`       | Server is unreachable       |
| `SocketTimeoutException` | Connection took too long    |
| `IOException`            | General network I/O failure |

---

# Final Key Takeaways

| Rule                                | Meaning                            |
| ----------------------------------- | ---------------------------------- |
| Fail Fast                           | Detect errors as early as possible |
| Handle Only What You Can            | Do not catch everything blindly    |
| Use Meaningful Exception Messages   | Makes debugging easier             |
| Use `finally` or Try-With-Resources | Avoid leaked resources             |
| Avoid Runtime Exceptions by Logic   | Fix your code, not the symptoms    |

**Good exception handling = stable, maintainable, predictable software.**
