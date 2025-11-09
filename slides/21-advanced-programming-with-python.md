---
marp: true
theme: default
paginate: true
backgroundColor: #ffffff
color: #000000
header: "![height:25](https://cdn.shraif.ir/cdn/main/ap/sharif-logo-blue.png) **Advanced Programming (AP) — Python Advanced Concepts**"
footer: "**Sharif University of Technology** • Fall 2025 • Instructor: Ali Najimi • Author: Hossein Masihi"
style: |
  :root { --brand:#1966ab; --text:#000; }
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
  .cols { display:grid;grid-template-columns:1.3fr 0.7fr;gap:28px;align-items:start; }
  .imgbox { border:1px solid #eee;padding:8px;border-radius:10px;text-align:center;animation:zoomIn 1s ease-in; }
  .imgbox img { border-radius:10px;border:3px solid #1966ab; }
  @keyframes fadeIn { from{opacity:0;transform:translateY(10px);} to{opacity:1;transform:translateY(0);} }
  @keyframes slideUp { from{opacity:0;transform:translateY(20px);} to{opacity:1;transform:translateY(0);} }
  @keyframes zoomIn { from{opacity:0;transform:scale(0.9);} to{opacity:1;transform:scale(1);} }
---

<!-- _class: lead -->
![bg right:30% 90%](https://cdn.shraif.ir/cdn/main/ap/sharif-logo-blue.png)
# Advanced Programming with Python

## OOP • ORM • Frameworks • Django Architecture

**Instructor:** Ali Najimi  
**Author:** Hossein Masihi  
Sharif University of Technology — Fall 2025

---

# OOP in Python — Concept

* Python is **object-oriented**: everything is an **object**.
* OOP supports:
  - Encapsulation
  - Inheritance
  - Polymorphism
  - Abstraction

```python
class Animal:
    def sound(self):
        pass

class Dog(Animal):
    def sound(self):
        return "Woof"
```

> Python OOP is flexible and dynamic compared to Java’s strict class model.

---

# OOP in Python — Pros & Cons

| Pros | Cons |
|------|------|
| Very flexible and dynamic | Too much flexibility can reduce safety |
| Easy to write and extend | Performance slower than compiled languages |
| Multiple inheritance supported | Can lead to complex inheritance chains |
| Duck typing simplifies interfaces | Run-time errors if used incorrectly |

> Python prioritizes **developer productivity** over strict type safety.

---

# ORM — Object Relational Mapping

* ORM maps **classes ↔ database tables**
* You interact with **objects**, not raw SQL.

```python
class Student(models.Model):
    name = models.CharField(max_length=50)
    age = models.IntegerField()
```

Internally converts:
```sql
SELECT * FROM student;
```

Benefits:
* Faster development
* Database abstraction
* Prevents SQL injection

Trade-offs:
* Slight performance overhead

---

# Popular Python Frameworks

| Purpose | Frameworks |
|--------|------------|
| Web (Full-stack) | **Django**, **Flask**, **FastAPI** |
| Data Science | NumPy, Pandas, SciPy |
| Machine Learning | TensorFlow, PyTorch, Scikit-Learn |
| Automation | Selenium, Scrapy |

> Python thrives in backend, AI/ML, scripting, and data-driven applications.

---

# Django — Overview

* Django is a **high-level web framework** following the **MVT pattern**:
  - **Model**: Database layer (ORM)
  - **View**: Business logic
  - **Template**: UI layer (HTML rendering)

```text
User Request → URL Router → View → Model → Template → Response
```

> Django encourages **clean architecture**, **reusable apps**, and **secure defaults**.

---

# Django — MVC vs MVT

| MVC Term | Django Term | Meaning |
|---------|-------------|---------|
| Model | Model | Data / ORM Layer |
| View | Template | Presentation layer |
| Controller | View (Function/Class) | Logic & request handling |

Why different naming?
* Django handles **controller logic internally** via its URL routing and middleware.

---

# Example Django View

```python
from django.shortcuts import render
from .models import Student

def home(request):
    students = Student.objects.all()
    return render(request, "home.html", {"students": students})
```

**Where errors likely occur:**
| Error | Cause |
|------|------|
| `DoesNotExist` | Query returned no object |
| `OperationalError` | Database connection issue |
| `TemplateDoesNotExist` | Wrong template name/path |
| `FieldError` | Incorrect model field name |

---

# Summary

| Concept | Key Idea |
|--------|----------|
| Python OOP | Dynamic, flexible object model |
| ORM | Maps classes to database tables |
| Frameworks | Django for full-stack, Flask/FastAPI for lightweight APIs |
| Django MVT | Model (data) / View (logic) / Template (UI) |

> Python enables rapid development with readable, scalable, and maintainable design patterns.

---

<!-- _class: lead -->
# Thank You!

**Advanced Programming — Sharif University — Fall 2025**
