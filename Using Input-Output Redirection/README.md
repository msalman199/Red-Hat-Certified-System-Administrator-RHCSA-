# Using Input-Output Redirection

This repository contains a comprehensive guide to understanding and implementing input-output streams, pipe chaining, and error handling mechanics in a Linux and containerized environment.

## 🎯 Objectives
By the end of this lab, you will be able to:
* **Route Data Streams:** Implement baseline output redirection using `>` and `>>`.
* **Chain Operations:** Utilize pipeline operators (`|`) to interconnect commands for efficient on-the-fly data processing.
* **Isolate Failures:** Segregate and redirect system error messages via standard error (`2>`) handles.
* **Orchestrate Complex Pipelines:** Combine diverse redirection techniques to execute advanced terminal and container workflows.

## 📋 Prerequisites
* **Environment:** A functional physical or virtual Linux system.
* **Utilities:** Access to a terminal shell loaded with standard GNU utility applications.
* **Containers:** `Podman` installed and configured to execute container-specific validation tasks.
* **Skills:** Ground-level familiarity with standard Linux terminal environments.

### ⚙️ Lab Setup
Open your terminal window and verify that your system matches the structural requirements:
```bash
uname -a
podman --version
```

---

## 🛠️ Step-by-Step Implementation

### Task 1: Output Redirection

#### Subtask 1.1: Basic Output Redirection (`>`)
Generate a baseline document using primary output standard stream routing:
```bash
echo "Hello, Red Hat OpenShift!" > greeting.txt
```
Verify the file creation and internal content:
```bash
cat greeting.txt
```
* **Expected Output:** `Hello, Red Hat OpenShift!`

Overwrite the target file to observe direct volume replacement behaviors:
```bash
echo "New content replaces old" > greeting.txt
cat greeting.txt
```
> ⚠️ **Key Concept:** The `>` operator initializes a brand-new file tracking point or completely overwrites pre-existing data blocks without warning.

#### Subtask 1.2: Appending Output (`>>`)
Inject data blocks directly into the bottom of documents without corrupting existing lines:
```bash
echo "Additional line" >> greeting.txt
echo "Line 3" >> greeting.txt
echo "Line 4" >> greeting.txt
```
Verify the composite log growth:
```bash
cat greeting.txt
```
* **Expected Output:**
  ```text
  New content replaces old
  Additional line
  Line 3
  Line 4
  ```
* **Troubleshooting Tip:** If lines are missing, verify that you applied the double arrow `>>` operation instead of the destructive single `>` sign.

---

### Task 2: Using Pipes

#### Subtask 2.1: Basic Pipe Usage
Interconnect standard outputs directly into matching standard inputs to chain calculations:
```bash
# Filter file listings matching specific strings
ls -l | grep "greeting"

# Extract file metrics by counting lines
cat greeting.txt | wc -l

# Build an advanced pipeline checking for target runtime engines
ps aux | grep podman | wc -l
```
* **Pipeline Explanation:** The command isolates process counters by listing all system processes (`ps aux`), isolating active container engines (`grep podman`), and summarizing the total count line metrics (`wc -l`).

#### Subtask 2.2: Advanced Pipe Operations
Sort structural records alphabetically:
```bash
cat greeting.txt | sort
```
Save your clean sorted array definitions out to an external file:
```bash
cat greeting.txt | sort > sorted_greeting.txt
```
##### 🦭 Podman Container Example
Isolate core container assets while actively stripping down clutter or empty placeholder values:
```bash
podman images | grep -v "<none>"
```

---

### Task 3: Error Redirection

#### Subtask 3.1: Redirecting Standard Error (`2>`)
Generate broken execution parameters and drop the corresponding fault log strings into file storage:
```bash
ls /nonexistent 2> error.log
cat error.log
```
Split normal data indicators (`stdout`) away from tracking errors (`stderr`) simultaneously:
```bash
ls /nonexistent /etc/passwd > output.log 2> error.log
```
Inspect both files to verify stream split paths:
```bash
cat output.log
cat error.log
```

#### Subtask 3.2: Advanced Error Handling
Merge both normal streams and terminal errors together inside a singular workspace registry tracking point:
```bash
ls /nonexistent /etc/passwd &> combined.log
```
Mute terminal system error outputs entirely by dropping stream segments into the system black hole:
```bash
ls /nonexistent 2> /dev/null
```
##### 🦭 Podman Container Example
Isolate infrastructure problems during unexpected script breaks within runtime application containers:
```bash
podman run --name testcontainer alpine /bin/false 2> container_error.log
cat container_error.log
```

---

### Task 4: Combined Operations

#### Subtask 4.1: Complex Redirection
Isolate successful executions away from unexpected framework execution problems:
```bash
(ls /etc/passwd /nonexistent | wc -l > success.log) 2> fail.log
```
Review the segmented pipeline results:
```bash
cat success.log
cat fail.log
```

#### Subtask 4.2: Practical Application
Consolidate runtime variables together to spin up a unified diagnostic text report:
```bash
{
  echo "=== System Report ==="
  date
  echo "=== Memory ==="
  free -h
  echo "=== Disk Usage ==="
  df -h
} > system_report.txt 2> system_errors.log
```
##### 🦭 Podman Container Example
Automate clean reporting across live local active cluster engines:
```bash
{
  echo "=== Container Images ==="
  podman images
  echo "=== Running Containers ==="
  podman ps
} > container_report.txt 2> container_errors.log
```

---

## 🔬 Skills Verification
Validate your command-line workflow skills by running this verification string:
```bash
(echo "Lab Verification"; ls /etc/passwd | wc -l; podman images 2>/dev/null | wc -l) > verification.txt
```
Review the contents of `verification.txt` to confirm your outputs are properly formatted.

---

## 🏁 Conclusion
By finishing these tasks, you have mastered foundational patterns for:
* Automating enterprise application deployments inside **Red Hat OpenShift** infrastructures.
* Gathering, managing, and parsing large-scale **container logs**.
* Constructing durable, production-grade **shell scripting blocks**.

---
_This workflow lab leverages open-source utilities matching validation guidelines within the Red Hat certification pathways._
