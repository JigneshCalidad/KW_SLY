# Module 5: GIT Version Control

## 🌱 Why This Module Matters

Version control isn't just about tracking changes—it's about **collaboration, safety, and history**. GIT enables you to:
- Work without fear (you can always go back)
- Collaborate effectively (multiple people, same codebase)
- Experiment safely (branches let you try things)
- Track what changed and why (commit messages tell stories)

For testers, GIT is essential because:
- Test code needs version control
- You'll collaborate with developers
- You need to track test changes
- Automation code is code—it needs management

---

## 📚 Learning Objectives

By the end of this module, you will understand:

1. **GIT Introduction** - What version control is and why it matters
2. **GIT Clone** - Getting code from repositories
3. **GIT Checkout** - Switching between versions/branches
4. **GIT Commit** - Saving changes
5. **GIT Push** - Sharing changes
6. **GIT Pull Request** - Collaborating through code review
7. **Merge Conflicts** - Resolving conflicts when changes overlap

---

## 🧩 Conceptual Overview

### GIT Introduction

**What GIT is**: Distributed version control system.

**Key concepts**:
- **Repository (repo)**: Project folder with version history
- **Commit**: Snapshot of changes at a point in time
- **Branch**: Parallel line of development
- **Remote**: Repository on server (GitHub, GitLab)

**Why it matters**:
- **History**: See what changed and when
- **Safety**: Can revert to any previous state
- **Collaboration**: Multiple people work on same code
- **Experimentation**: Try things without breaking main code

**Analogy**: Like a time machine for your code—you can go back to any point.

---

### GIT Clone

**What it does**: Creates a local copy of a remote repository.

**Syntax**:
```bash
git clone <repository-url>
```

**Example**:
```bash
git clone https://github.com/user/project.git
```

**What happens**:
- Downloads entire repository
- Creates local copy with full history
- Sets up connection to remote (origin)

**Use case**: Getting code from GitHub/GitLab to work on locally.

---

### GIT Checkout

**What it does**: Switch between branches or commits.

**Syntax**:
```bash
git checkout <branch-name>
git checkout <commit-hash>
```

**Common uses**:
- Switch branches: `git checkout feature-branch`
- Create and switch: `git checkout -b new-branch`
- View old version: `git checkout <commit-hash>`

**Concept**: Like switching between different versions of your project.

---

### GIT Commit

**What it does**: Saves a snapshot of your changes.

**Workflow**:
1. **Make changes** to files
2. **Stage changes**: `git add <file>` or `git add .`
3. **Commit**: `git commit -m "Message describing changes"`

**Key concepts**:
- **Staging area**: Prepares changes for commit
- **Commit message**: Describes what and why (important!)
- **Commit hash**: Unique identifier for each commit

**Example**:
```bash
git add test_login.java
git commit -m "Add login test case"
```

**Best practices**:
- Commit often (logical units of work)
- Write clear commit messages
- One logical change per commit

---

### GIT Push

**What it does**: Uploads local commits to remote repository.

**Syntax**:
```bash
git push <remote> <branch>
```

**Example**:
```bash
git push origin main
```

**What happens**:
- Sends your commits to remote
- Updates remote branch
- Others can see your changes

**Use case**: Sharing your work with team.

---

### GIT Pull Request

**What it is**: Request to merge your changes into main branch.

**Workflow**:
1. Create feature branch
2. Make changes, commit
3. Push branch to remote
4. Create Pull Request (PR) on GitHub/GitLab
5. Team reviews
6. Merge if approved

**Purpose**:
- **Code review**: Others check your code
- **Discussion**: Talk about changes
- **Quality**: Catch issues before merging
- **History**: Record of why changes were made

**Testing perspective**: PRs are where test code gets reviewed.

---

### Merge Conflicts Resolution

**What they are**: When two people change the same lines differently.

**When they happen**:
- Two branches modify same code
- Merging branches with conflicts
- Pulling changes that conflict with yours

**How to resolve**:
1. **Identify conflict**: GIT marks conflicted areas
2. **Edit file**: Choose which version (or combine)
3. **Mark resolved**: `git add <file>`
4. **Complete merge**: `git commit`

**Conflict markers**:
```
<<<<<<< HEAD
Your changes
=======
Their changes
>>>>>>> branch-name
```

**Resolution**: Edit to keep what you want, remove markers.

**Best practices**:
- Pull frequently (reduce conflicts)
- Communicate with team
- Test after resolving

---

## 🎯 Key Takeaways

1. **GIT tracks history** - Every change is recorded
2. **Commits are snapshots** - Save logical units of work
3. **Branches enable experimentation** - Try things safely
4. **Pull Requests enable collaboration** - Code review and discussion
5. **Conflicts are normal** - Learn to resolve them

---

## 📝 Exercises

See `exercises/` folder for hands-on practice.

---

## 🔗 Connections to Other Modules

- **Module 6+**: All automation code should be in GIT
- **Module 10**: CI/CD uses GIT for automation

---

**Reflection Question**: How does version control change how you approach writing and maintaining test code?

