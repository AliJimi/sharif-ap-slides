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
  h1, h2, h3 { color: var(--brand); }
  code { background: #f3f3f3; padding: 4px 6px; border-radius: 6px; }
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
sudo apt install git                              # Install Git on Debian/Ubuntu
git config --global user.name "Hossein Masihi"    # Set your global username
git config --global user.email "hossein@sharif.ir" # Set your global email

git config --global init.defaultBranch main       # Set default branch name to main
git config --global pull.rebase false             # Disable automatic rebase on pull
git config --list                                 # View current Git configuration
````

---

# Core Concepts

* **Repository:** the project directory tracked by Git
* **Commit:** a snapshot of your changes
* **Branch:** independent line of development
* **Merge:** combining changes from different branches
* **Remote:** shared repo (GitHub/GitLab)

---

# Basic Workflow

```bash
mkdir project && cd project       # Create a new project directory
git init                          # Initialize an empty Git repository
echo "# My Project" > README.md   # Create a README file
git add .                         # Stage all changes for commit
git commit -m "Initial commit"    # Save snapshot with a message
git status                        # Check status of working tree
git log --oneline --graph         # Show concise commit history with graph
```

---

# Branching and Merging

```bash
git branch feature/login          # Create a new branch named feature/login
git switch feature/login          # Switch to that branch
# make code changes...
git add . && git commit -m "Add login feature"  # Commit your changes
git switch main                   # Switch back to main branch
git merge feature/login           # Merge login branch into main
```

✅ Keep branches small & focused.
💬 Use **Pull Requests** for code review before merging.

---

# Remote Repositories

```bash
git remote add origin https://github.com/user/repo.git  # Link local repo to remote
git push -u origin main                                # Push local commits to remote
git pull                                               # Fetch and merge latest changes
```

🔒 Prefer **SSH keys** instead of HTTPS for secure authentication.

---

# Conflict Resolution

```bash
# After a merge conflict occurs:
git status                # Check which files are in conflict
# Open those files, fix conflict manually
git add <file>            # Mark conflict as resolved
git commit                # Finalize the merge
```

💡 Tip: Make small commits and pull frequently to avoid conflicts.

---

# Rewriting History Safely

```bash
git revert <commit>            # Create new commit that undoes changes of a specific commit
git reset --soft <commit>      # Move HEAD, keep changes staged
git reset --hard <commit>      # Discard all changes — use with caution!
```

⚠️ Never run `reset --hard` on shared branches (it rewrites history).

---

# Best Practices

* Write **clear, meaningful commit messages**
* Keep feature branches **short-lived**
* Use `.gitignore` to avoid tracking unnecessary files
* Tag stable releases

```bash
git tag -a v1.0.0 -m "First stable release"  # Create annotated tag
git push origin v1.0.0                       # Push tag to remote
```

---

# Summary & Resources

✅ Git helps you **track changes**, **collaborate**, and **restore versions**
✅ Typical flow:
→ edit → add → commit → push/pull

---

## 📚 Official Resources

* 📖 [Pro Git (Free Book)](https://git-scm.com/book/en/v2?utm_source=chatgpt.com)
* 🧭 [Git Documentation](https://git-scm.com/docs?utm_source=chatgpt.com)
* 📘 [Git Tutorial — Atlassian](https://www.atlassian.com/git/tutorials?utm_source=chatgpt.com)

---

## 🌐 Interactive & Visual Learning

| Site                                                                                                       | Description                                                                    |
| ---------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| [**Learn Git Branching**](https://learngitbranching.js.org/?utm_source=chatgpt.com)                        | Interactive visual Git playground for learning branching, merging, and rebase. |
| [**Visual Git Guide**](https://marklodato.github.io/visual-git-guide/index-en.html?utm_source=chatgpt.com) | Graphical reference for Git operations.                                        |
| [**Git School — Visualizing Git**](https://git-school.github.io/visualizing-git/?utm_source=chatgpt.com)   | Visual tool for understanding HEAD, commits, and merges.                       |
| [**Oh My Git!**](https://ohmygit.org/?utm_source=chatgpt.com)                                              | Open-source game to learn Git concepts through visualization.                  |

---

<!-- _class: lead -->

# End of Presentation

<div class="imgbox">
  <img src="../assests/slides/git/meme.png" alt="Git Meme" width="260">
</div>

*Sharif University Workshop Series — Git Fundamentals*
