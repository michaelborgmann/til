# Git Commit Conventions

The popular **Git Commit Conventions** help keep commit history **structured, readable, and meaningful**. Using a standard like **Conventional Commits** makes it easier to:

* Understand *what changed* at a glance
* Generate changelogs automatically
* Track features, fixes, and breaking changes
* Collaborate consistently with others

Simply start your commits with a **type**, optionally a **scope**, a **short summary**, and optionally a **body/footer**.

---

## **1. Structure**

```
<type>(optional-scope): <short summary>
(optional body)
(optional footer)
```

---

## **2. The commit types**

### **feat** — a new feature

> Adds new behavior.
> **Example:**
> `feat(user-auth): add login via email`

### **fix** — a bug fix

**Example:**
`fix(api): handle timeout errors properly`

### **docs** — documentation changes

**Example:**
`docs: clarify installation instructions`

### **style** — formatting, no code logic changes

(e.g., spacing, renaming variables for clarity)
**Example:**
`style: reformat code according to style guide`

### **refactor** — restructuring code without changing behavior

**Example:**
`refactor(database): simplify query logic`

### **perf** — performance improvements

**Example:**
`perf(search): speed up results filtering`

### **test** — adding or fixing tests

**Example:**
`test: add coverage for edge cases in validation`

### **chore** — project maintenance

(build scripts, dependencies, config files)
**Example:**
`chore: update dependencies`

---

## **3. Optional extras**

### **Scope**

Useful for multi-module projects.
Example:
`feat(auth): add password reset`

### **Body**

Explain *why* and *how*, especially for complex fixes.

```
fix: prevent duplicate entries in user list

Previously, duplicate entries were possible when importing
data concurrently. Added a uniqueness check to resolve.
```

### **Footer**

For breaking changes or issue links:

```
BREAKING CHANGE: API now requires token authentication.
Closes #42
```

---

## **4. Super-short mnemonic**

**F F D S R P T C**
*Feat, Fix, Docs, Style, Refactor, Perf, Test, Chore*

Or even shorter:

**Features, Fixes, and Everything Else.**

**Pro tip:** Always aim for a **short**, **clear first line**. Body and footer are optional.
