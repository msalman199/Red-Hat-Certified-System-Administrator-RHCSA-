# Managing File Permissions (ugo/rwx)

This repository contains a comprehensive guide to understanding and manipulating POSIX file permissions, user groups, and asset ownership boundaries on Linux file systems.

## 🎯 Objectives
By the end of this lab, you will be able to:
* **Decode Permission Matrices:** Read and interpret standard security attribute strings.
* **Manipulate Access Strings:** Toggle execution masks using symbolic and numeric (`octal`) flags via `chmod`.
* **Alter Asset Ownership:** Shift operational identity boundaries using `chown` and `chgrp`.
* **Harden Host Systems:** Practice privilege isolation patterns to secure file resources.

## 📋 Prerequisites
* **OS:** Any modern Linux operating system instance (Ubuntu, CentOS, Fedora, RHEL).
* **Environment:** Access to an interactive terminal emulator window.
* **Privileges:** A standard user profile account equipped with `sudo` administrative delegation rules.

---

## 🛠️ Step-by-Step Implementation

### Task 1: View File Permissions with ls -l

#### Step 1: List Files with Detailed Permissions
Query your active directory using the long listing layout format modifier to expose hidden system security bits:
```bash
ls -l
```
* **Expected Output Structure:**
  ```text
  -rw-r--r-- 1 user group 1024 Jun 10 10:00 example.txt
  drwxr-xr-x 2 user group 4096 Jun 10 10:01 directory
  ```

#### Step 2: Interpret Permission Strings
Deconstruct the leading 10-character string blocks from your terminal printout:
* **File Type Indicator (Position 1):**
  * `-` represents a standard regular file target block.
  * `d` represents an operational system directory folder node.
* **Access Triads (Positions 2–10):**
  * `rw-` (Positions 2–4): **User / Owner** rules grid. (Read & Write permissions).
  * `r--` (Positions 5–7): **Group** access mask profile. (Read-Only access).
  * `r--` (Positions 8–10): **Others / Global** ring layer. (Read-Only access).

> 💡 **Core Reference Model:** `u` (User), `g` (Group), `o` (Others) map precisely down onto `r` (Read), `w` (Write), `x` (Execute).

---

### Task 2: Change File Permissions Using chmod

#### Step 1: Change Permissions Symbolically
Inject execute permissions onto the primary file owner block without modifying group or global rules:
```bash
chmod u+x example.txt
```
Verify structural attribute modifications:
```bash
ls -l example.txt
```
* **Expected Output:** `-rwxr--r-- 1 user group 1024 Jun 10 10:00 example.txt`

#### Step 2: Change Permissions Numerically
Apply absolute octal mask overrides to establish standard `rw-r-----` rules structures across all user rings instantly:
```bash
chmod 640 example.txt
```
Verify the numeric state transformation:
```bash
ls -l example.txt
```
* **Expected Output:** `-rw-r----- 1 user group 1024 Jun 10 10:00 example.txt`

> 💡 **Octal Math Matrix:** `Read = 4` | `Write = 2` | `Execute = 1`
> * `6` ($4+2+0$) $\rightarrow$ User receives Read + Write.
> * `4` ($4+0+0$) $\rightarrow$ Group receives Read-Only.
> * `0` ($0+0+0$) $\rightarrow$ Global ring drops all access privileges.

* **Troubleshooting Tip:** If commands stall or return error blocks, prefix adjustments with `sudo` to force system rule rewrites.

---

### Task 3: Modify File Ownership Using chown and chgrp

#### Step 1: Change File Owner
Shift the primary administrative assignment boundary mapping of an asset over to a secondary system user profile (e.g., `newuser`):
```bash
sudo chown newuser example.txt
```
Verify ownership allocation shifts:
```bash
ls -l example.txt
```
* **Expected Output:** `-rw-r----- 1 newuser group 1024 Jun 10 10:00 example.txt`

#### Step 2: Change File Group
Migrate the secondary collaborative access group layer tracking mask over to an alternative target system group definition (e.g., `newgroup`):
```bash
sudo chgrp newgroup example.txt
```
Verify structural target group mutations:
```bash
ls -l example.txt
```
* **Expected Output:** `-rw-r----- 1 newuser newgroup 1024 Jun 10 10:00 example.txt`
> 💡 **Short-Cut Hint:** You can change both owners and group properties inside a single, unified execution string using a colon separator: `sudo chown user:group filename`.

---

## 🔒 Security Best Practices
* **Confidentiality:** Lock down private data tracking tokens or encryption keys completely using strict masks: `chmod 600 sensitive.dat`.
* **Minimize Attack Surface:** Avoid wide-open system rules layout assignments. Using `chmod 777` exposes systems to severe privilege escalation attacks.
* **Collaborative Structuring:** Align team resource paths to targeted system groups using `chgrp` rather than modifying global access rings.

## 🏁 Conclusion
By executing this lab track layout, you have mastered:
* Auditing host target parameters visually via long-listing patterns.
* Flipping security masks systematically via octal and symbolic methods.
* Updating multi-user tenancy boundary states via ownership shifts.

These identity controls form the core foundational building blocks of security layouts within distributed infrastructure systems and enterprise application platforms like **Red Hat OpenShift**.

## 🚀 Next Steps
* Learn how to push security constraints down through nested directory structures recursively via `chmod -R`.
* Explore enterprise file-sharing access models by researching Access Control Lists (`ACLs`).
