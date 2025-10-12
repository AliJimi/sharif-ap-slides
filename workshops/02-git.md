---
marp: true
theme: default
paginate: true
backgroundColor: #ffffff
color: #000000
header: "![height:24](/assests/sharif-logo-blue.png) **Sharif University Workshop Series — Git Fundamentals**"
footer: "**Sharif University of Technology** • Fall 2025 • Mr. Ali Najimi • Hossein Masihi"
style: |
  :root { --brand: #1966ab; --text: #000000; }
  section { background-color: #ffffff; color: var(--text); font-size: 28px; font-family: "Inter","Segoe UI","Roboto","Helvetica Neue",Arial,sans-serif; }
  h1, h2, h3 { color: var(--brand); font-family: "Inter","Segoe UI","Roboto","Helvetica Neue",Arial,sans-serif; }
  ul { margin-top: 10px; }
  .cols { display: grid; grid-template-columns: 1.2fr 0.8fr; gap: 28px; align-items: start; }
  .imgbox { border: 1px solid #eee; padding: 8px; border-radius: 10px; text-align:center; }
  .imgbox img { border-radius: 10px; border: 3px solid #1966ab; }
  section.lead header, section.lead footer { display: none !important; }
---

<!-- _class: lead -->
![bg right:30% 90%](../assests/sharif-logo-blue.png)
# Advanced Programming
## Git Fundamentals


**Instructor:** Ali Najimi
**Lecturer:**  Hossein Masihi
**Department of Computer Engineering**  
**Sharif University of Technology**  
**Fall 2025**

---

# Table of Contents
1. What is Git?  
2. Installation & Setup  
3. Core Concepts  
4. Basic Workflow  
5. Branching and Merging  
6. Remote Repositories  
7. Conflict Resolution  
8. Rewriting History Safely  
9. Best Practices  
10. Summary & Resources  

---

# What is Git?
- Distributed Version Control System (DVCS)  
- Tracks every change in your project  
- Enables collaboration between multiple developers  
- Fast, efficient, and reliable

---

# Installation & Setup

```bash
sudo apt install git

git config --global user.name "Hossein Masihi"
git config --global user.email "hossein@sharif.ir"

git config --global init.defaultBranch main
git config --global pull.rebase false
git config --list
```

---

# Core Concepts

* **Repository:** a version-controlled project directory
* **Commit:** a snapshot of changes
* **Branch:** an independent line of development
* **Merge:** combining work from branches
* **Remote:** a shared repository on GitHub/GitLab

---

# Basic Workflow

```bash
mkdir project && cd project
git init
echo "# My Project" > README.md
git add .
git commit -m "Initial commit"
git status
git log --oneline --graph
```

---

# Branching and Merging

```bash
git branch feature/login
git switch feature/login
# work on your feature
git switch main
git merge feature/login
```

Keep branches small and focused. Use Pull Requests for code review.

---

# Remote Repositories

```bash
git remote add origin https://github.com/user/repo.git
git push -u origin main
git pull
```

Prefer **SSH keys** for authentication over HTTPS for security and convenience.

---

# Conflict Resolution

```bash
# After merge conflict:
git status
# open conflicted files, resolve manually
git add <file>
git commit
```

Tip: keep commits small and sync frequently to reduce conflicts.

---

# Rewriting History Safely

```bash
# Safely revert a commit
git revert <commit>

# Move HEAD (use with care)
git reset --soft <commit>
git reset --hard <commit>
```

* Never `reset --hard` on a shared branch.

---

# Best Practices

* Write clear, meaningful commit messages
* Keep feature branches short-lived
* Use `.gitignore` properly
* Tag releases for stable versions

```bash
git tag -a v1.0.0 -m "First stable release"
git push origin v1.0.0
```

---

# Summary & Resources

* Git enables teamwork and code history management
* Typical flow: **edit → add → commit → push/pull**
* Practice daily — it becomes second nature

**References:**

* git-scm.com/docs
* learngitbranching.js.org
* Atlassian Git Tutorials
* *Pro Git* (Free Book)

---

<!-- _class: lead -->

# End of Presentation

<div class="imgbox">
  <img src="../assests/slides/git/meme.png" alt="Git Meme" width="260">
</div>

*Sharif University Workshop Series — Git Fundamentals*
