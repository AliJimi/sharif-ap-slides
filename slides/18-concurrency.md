---
marp: true
theme: default
paginate: true
backgroundColor: #ffffff
color: #000000
header: "![height:25](https://cdn.shraif.ir/cdn/main/ap/sharif-logo-blue.png) **Advanced Programming (AP) — Concurrency in Java**"
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
---

<!-- _class: lead -->
![bg right:30% 90%](https://cdn.shraif.ir/cdn/main/ap/sharif-logo-blue.png)
# Advanced Programming
## Concurrency — Multithreading in Java

**Instructor:** Ali Najimi
**Author:** Hossein Masihi
**Department of Computer Engineering**  
**Sharif University of Technology**  
**Fall 2025**

---

<div class="imgbox">

![width:850](assets/17/concurrency-thanks.png)
</div>

---
# Concurrency — Concept

* **Concurrency** allows multiple tasks to progress **overlapping in time**.
* In Java, concurrency is primarily achieved using **Threads**.
* Useful for:
  - Parallel computation
  - Responsive UI
  - Server handling multiple clients

```java
class MyThread extends Thread {
    public void run() {System.out.println("Running in parallel!"); }
    }
````

> Concurrency ≠ Parallelism
> (parallelism requires multiple CPU cores)

---

# Creating Threads

### Extending `Thread`

```java
class Worker extends Thread {
    public void run() {
        System.out.println("Thread running");
    }
}
new Worker().start();
```
---

### Implementing `Runnable`

```java
class Worker implements Runnable {
    public void run() {
        System.out.println("Running");
    }
}
new Thread(new Worker()).start();
```

> Always use `start()`, never call `run()` directly.

---

# Thread Life Cycle

| State             | Meaning                        |
| ----------------- | ------------------------------ |
| New               | Thread created but not started |
| Runnable          | Ready to run or running        |
| Blocked / Waiting | Waiting for a resource / event |
| Timed Waiting     | Waiting for a specified time   |
| Terminated        | Execution finished             |

---

<div class="imgbox">
<h1>Thread Lifecycle</h1>

![width:800](assets/17/thread-lifecycle.png)

</div>

---

# Synchronization — Why?

Multiple threads accessing shared data simultaneously can cause **race conditions**.

Example of incorrect behavior:

```java
class Counter {
    int value = 0;
    void increment() { value++; }
}
```

Two threads running increment() may **overwrite each other** → wrong results.

---

# Synchronization — Solution

```java
class Counter {
    private int value = 0;

    synchronized void increment() {
        value++;
    }

    synchronized int getValue() {
        return value;
    }
}
```

* `synchronized` ensures **mutual exclusion**.
* Only one thread can run the synchronized method at a time.

> Synchronization prevents **race conditions** but reduces performance.

---

# Critical Section

* A **Critical Section** is code that accesses **shared data**.
* It must be executed **atomically** (one thread at a time).

Identifying critical section:

```java
balance = balance - amount;
```

**If not synchronized → corrupted financial transactions.**

---

**Errors that occur here:**

| Error           | Cause                                       |
| --------------- | ------------------------------------------- |
| Race Condition  | Two threads update shared data at same time |
| Data Corruption | Intermediate state becomes visible          |
| Lost Update     | One write overwrites the other              |

---

# Locks — More Control

```java
import java.util.concurrent.locks.*;

class Account {
    private Lock lock = new ReentrantLock();
    private int balance;

    void withdraw(int amount){
        lock.lock();
        try { balance -= amount; } finally { lock.unlock(); }
    }
}
```

`Lock` provides:

* `tryLock()` → avoid deadlock
* More flexibility than `synchronized`

---

# Deadlock — When Threads Block Each Other

Occurs when two threads wait forever for resources held by each other.

```text
Thread A waits for resource X → held by Thread B
Thread B waits for resource Y → held by Thread A
```

> Avoid holding multiple locks at the same time when possible.

---

# Summary

| Concept           | Key Idea                                   |
| ----------------- | ------------------------------------------ |
| Concurrency       | Overlapping execution of tasks             |
| Thread Life Cycle | States from creation → termination         |
| Synchronization   | Prevents race conditions                   |
| Critical Section  | Code accessing shared data                 |
| Locks             | Give more granular control                 |
| Goal              | Safe and efficient multi-threaded programs |

---

<!-- _class: lead -->

# Thank You!

<div class="cols">
<div>
<p class="pill">Concurrency — Safe Multithreading</p>
</div>
<div class="imgbox">

![width:850](assets/17/thanks.png)
</div>
</div>

**Sharif University of Technology — Advanced Programming — Fall 2025**
