# Creating and Editing Text Files

This repository contains a comprehensive, hands-on guide to mastering Linux text manipulation utilities. You will develop practical proficiency in terminal-based editors (`vi` and `nano`), handle raw file streams, identify line-ending architectures, and construct functional system configuration files.

## 🎯 Objectives
By the end of this lab, you will be able to:
* **Navigate Terminal Editors:** Smoothly control workspace workflows inside both `nano` and `vi`/`vim`.
* **Manipulate Text Data:** Perform basic entry, line deletion, and persistent file saving procedures.
* **Manage File Profiles:** Understand and modify file encoding parameters and newline standards (`LF` vs `CRLF`).
* **Audit Document Integrity:** Apply standard diagnostic commands to measure file sizes, structural counts, and hidden syntax layout anomalies.

## 📋 Prerequisites
* **OS:** A modern Linux-based environment (Fedora, RHEL, or CentOS recommended).
* **Access:** Standard user terminal shell access privileges.
* **Skills:** Ground-level comfort executing basic directory navigation workflows.

---

## 🛠️ Step-by-Step Implementation

### Task 1: Creating and Editing Files with nano

#### Subtask 1.1: Launching nano and Creating a File
Open your terminal emulator window and spin up a new document profile tracking stream:
```bash
nano first_file.txt
```
* **Interface Mechanics:** The lower horizontal margin reveals primary shortcuts (where the caret symbol `^` translates to holding down the `Ctrl` key). The pulsing cursor denotes an active text insertion space.

#### Subtask 1.2: Basic Text Operations
Input the following payload confirmation text block:
```text
Hello OpenShift!
This is my first text file.
```
##### ⚡ Efficiency Shortcut Layout
* `Ctrl + A`: Warp the cursor instantly back to the absolute starting point of your active line.
* `Ctrl + E`: Warp the cursor instantly out to the terminal boundary limit end of your line.

##### 💾 Save and Exit Sequence
1. Commit data to disk by hitting `Ctrl + O` (Write Out).
2. Tap `Enter` to lock in and confirm the existing file name assignment.
3. Terminate the editing program interface by typing `Ctrl + X`.

* **Expected Outcome:** `first_file.txt` compiles successfully directly inside your active operational directory.

---

### Task 2: Advanced Editing with vi

#### Subtask 2.1: Entering vi and Basic Modes
Initialize a secondary target file structure to explore advanced standard interface modes:
```bash
vi second_file.txt
```
> ⚠️ **Key Concept:** `vi` relies on mode transitions. On launch, you land in **Command Mode** (used for navigation and macro actions). You must explicitly transition modes to interact with content text blocks.

#### Subtask 2.2: Editing Operations
1. Shift into **Insert Mode** by tapping the `i` key on your keyboard.
2. Input the following sample container infrastructure configuration lines:
   ```text
   Podman Container Basics:
   1. Images
   2. Containers
   3. Pods
   ```
3. Return to **Command Mode** by tapping the `Esc` key once.
4. Delete line number 2 (`1. Images`):
   * Move your cursor directly down onto any character within that target row.
   * Type the shortcut command sequence `dd` consecutively.
5. Save changes and exit back to the shell prompt by entering:
   ```text
   :wq
   ```
   Followed instantly by tapping `Enter`.
* **Troubleshooting Tip:** If your terminal locks up or refuses typing inputs, tap the `Esc` key multiple times to flush stuck processing streams and return back to foundational Command Mode.

---

### Task 3: File Manipulation Commands

#### Subtask 3.1: Viewing File Contents
Print raw file components out onto the standard terminal output stream directly:
```bash
cat first_file.txt
```
For reading long files, pass the file into a clean paginated terminal reading application:
```bash
less second_file.txt
```
* *Press `q` at any point during less execution to quit out back to your prompt.*

#### Subtask 3.2: File Encoding and Line Endings
Inspect raw structure details and metadata characteristics hidden inside your file blocks:
```bash
file first_file.txt
```
* **Expected Output:** Typically identifies the profile layout as `ASCII text`.

##### 🔄 Line-Ending Format Transformations
Operating system architectures handle file carriage breaks differently. Unix defaults strictly to Line Feed (`LF` / `\n`), while Windows environments enforce Carriage Return Line Feed (`CRLF` / `\r\n`). Shift file parameters across styles with these translation wrappers:
```bash
# Convert standard Unix tracking layout over to target DOS formatting
unix2dos first_file.txt

# Strip DOS formatting elements and snap back down onto Unix profiles
dos2unix first_file.txt
```

---

### Task 4: Practical Application

#### Subtask 4.1: Create a Podman Configuration Snippet
Initialize a targeted mock container storage blueprint file:
```bash
nano podman_config.conf
```
Append the following system variables inside the workspace block, then save and close:
```ini
[storage]
driver = "overlay"
runroot = "/var/run/containers/storage"
graphroot = "/var/lib/containers/storage"
```

#### Subtask 4.2: Validate File Integrity
Audit file structural spacing layouts to verify that there are no empty hanging line-end anomalies:
```bash
grep -n '[[:space:]]\$' podman_config.conf
```
Verify aggregate layout sizing metrics by pulling a total line validation count check:
```bash
wc -l podman_config.conf
```

---

## 🔬 Verification
Run this validation audit execution loop to guarantee that all targeted lab documents exist with the correct system formatting rules:
```bash
ls -l *.txt *.conf
file *
```

## 🏁 Conclusion
By completing these lab exercises, you have mastered:
* Handling file operations fluently across both `nano` and `vi` terminal layers.
* Troubleshooting mode blockages and managing standard file operations.
* Correcting carriage differences to safeguard script transport across platforms.
* Organizing production-grade system configurations matching **Podman** and **Red Hat OpenShift** structural environments.

## 🚀 Next Steps
* Experiment with nesting complex structured parameters across multi-layer system sheets.
* Unlock advanced search/replace parameters inside `vi` by testing commands like `:%s/old/new/g`.
* Learn how modifying permission strings changes the editing access profiles of users.
