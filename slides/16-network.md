---
marp: true
theme: default
paginate: true
backgroundColor: #ffffff
color: #000000
header: "![height:25](https://cdn.shraif.ir/cdn/main/ap/sharif-logo-blue.png) **Advanced Programming (AP) — Networking & Sockets**"
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
## Networking & Socket Programming

**Instructor:** Ali Najimi  
**Author:** Hossein Masihi  
Sharif University of Technology — Fall 2025

---

# Table of Contents

1. What is Networking?  
2. IP, Ports, and Protocols  
3. Socket Programming Basics  
4. TCP vs UDP  
5. Client-Server Communication Model  
6. Example: Java Socket Server & Client  
7. Summary

---

# Networking — Concept

<div class="cols">
<div>

* **Networking** allows computers to communicate and share data.
* Communication happens through:
  - **IP Address** (identifies device)
  - **Port Number** (identifies application)
  - **Protocol** (rule of communication)

> Networking enables distributed systems and real-time applications.

</div>
<div>
  <div class="imgbox">
  ![width:850](assets/16/network-concept.png)
  </div>
</div>
</div>

---

# TCP vs UDP

| Feature | TCP | UDP |
|--------|-----|-----|
| Reliability | Guaranteed delivery | No delivery guarantee |
| Ordering | Maintains packet order | No ordering |
| Speed | Slower | Faster |
| Use Case | Web, Email, Banking | Streaming, VoIP, Games |

> TCP = Reliable.  
> UDP = Fast.

---

# What is a Socket?

* A **socket** is an endpoint for communication.
* Created on both **client** and **server**.
* The server listens on a **port** waiting for clients.

```

Client <----> Network <----> Server

````

> Sockets enable bidirectional communication.

---

# Client-Server Model

<div class="imgbox">
![width:900](assets/16/client-server.png)
</div>

* Server waits for requests  
* Client initiates communication  

---

# Example — Simple TCP Server (Java)

```java
import java.net.*;
import java.io.*;

public class Server {
    public static void main(String[] args) throws Exception {
        ServerSocket server = new ServerSocket(5000);
        Socket socket = server.accept();
        BufferedReader in = new BufferedReader(new InputStreamReader(socket.getInputStream()));
        System.out.println("Client says: " + in.readLine());
        server.close();
    }
}
````

---

# Example — Simple TCP Client (Java)

```java
import java.net.*;
import java.io.*;

public class Client {
    public static void main(String[] args) throws Exception {
        Socket socket = new Socket("localhost", 5000);
        PrintWriter out = new PrintWriter(socket.getOutputStream(), true);
        out.println("Hello Server!");
        socket.close();
    }
}
```

> Client connects → sends → server receives.

---

# Key Design Notes

| Concept               | Importance                     |
| --------------------- | ------------------------------ |
| Blocking I/O          | Calls wait until completion    |
| Multithreading Server | Supports multiple clients      |
| Resource Cleanup      | Always close streams & sockets |
| Protocol Design       | Agree on message format        |

---

# Summary

| Concept       | Description                     |
| ------------- | ------------------------------- |
| Network       | Enables remote communication    |
| Socket        | Endpoint for data transfer      |
| TCP           | Reliable, ordered communication |
| UDP           | Fast, lightweight communication |
| Client/Server | Fundamental interaction model   |

> Sockets enable everything from chat apps to distributed computing.

---

<!-- _class: lead -->

# Thank You!

<div class="cols">
<div>
<p class="pill">Networking & Sockets — Practical Foundations</p>
</div>
<div class="imgbox">
![width:850](assets/16/network-thanks.png)
</div>
</div>

**Sharif University of Technology — Advanced Programming — Fall 2025**
