# Creating Simple Shell Scripts

This repository contains a comprehensive, hands-on guide to automating tasks via Bash shell scripting. You will learn to construct executable scripts, manage variables, implement basic control flow logic (conditionals and loops), and systematically debug execution faults.

## 🎯 Objectives
By the end of this lab, you will be able to:
* **Construct Bash Scripts:** Write and execute basic automation files utilizing proper formatting rules.
* **Manage Shell Variables:** Assign, reference, and dynamically inject environment data into strings.
* **Implement Control Flow:** Orchestrate processing rules using conditional statements (`if`) and execution cycles (`for`).
* **Debug Faulty Scripts:** Isolate runtime errors and monitor logic steps using native tracing tools (`-x`).

## 📋 Prerequisites
* **OS:** A Linux-based operating system (e.g., Fedora, Ubuntu, CentOS, or RHEL) with the Bash shell available.
* **Text Editor:** Access to a terminal-based editor (e.g., `nano`, `vim`).
* **Skills:** Ground-level comfort executing basic command-line commands.

---

## 🛠️ Step-by-Step Implementation

### Task 1: Write a Simple Shell Script

#### Subtask 1.1: Create and Execute a Basic Script
Initialize a dedicated directory to keep your automation files organized:
```bash
mkdir ~/shell_scripts && cd ~/shell_scripts
```
Open a new document named `hello_world.sh` inside your editor:
```bash
nano hello_world.sh
```
Append the script block below. The **shebang** (`#!/bin/bash`) on line one forces the operating system to execute this file using the Bash interpreter:
```bash
#!/bin/bash
echo "Hello, World!"
```
Save the file and exit your editor (`Ctrl+O`, `Enter`, `Ctrl+X` in nano).

Grant execution permissions to transform the raw text block into an executable file:
```bash
chmod +x hello_world.sh
```
Run your script from the terminal prompt:
```bash
./hello_world.sh
```
* **Expected Output:** `Hello, World!`
* **Troubleshooting:** 
  * If you encounter a `Permission denied` error, verify that you applied the `chmod +x` modifier.
  * If execution fails completely, confirm the shebang (`#!/bin/bash`) sits exactly on line 1 without leading spaces.

#### Subtask 1.2: Execute Commands in a Script
Create a new file to consolidate multiple system evaluation utilities into an automated status script:
```bash
nano system_info.sh
```
Append the following logic block to read system states dynamically:
```bash
#!/bin/bash
echo "Current date: \$(date)"
echo "User: \$USER"
echo "Current directory: \$(pwd)"
```
Save your modifications, apply execution bits, and run the pipeline:
```bash
chmod +x system_info.sh
./system_info.sh
```
* **Expected Output Structure:**
  ```text
  Current date: [current date/time values]
  User: [your logged-in username]
  Current directory: [your active workspace directory path]
  ```

---

### Task 2: Variables and Control Flow

#### Subtask 2.1: Assign and Use Variables
Initialize a script file to study data assignments within the shell environment:
```bash
nano variables.sh
```
Add the data blocks below (do not insert spaces around the assignment `=` character):
```bash
#!/bin/bash
name="OpenShift Learner"
age=25
echo "Name: \$name, Age: \$age"
```
Lock in the adjustments, elevate permissions, and execute:
```bash
chmod +x variables.sh
./variables.sh
```
* **Expected Output:** `Name: OpenShift Learner, Age: 25`

#### Subtask 2.2: Use an `if` Statement
Create a checking script to branch your script's logic based on user roles:
```bash
nano check_user.sh
```
Append the following identity validation rule block:
```bash
#!/bin/bash
if [ "\$USER" == "root" ]; then
  echo "Running as root. Be cautious!"
else
  echo "Running as \$USER."
fi
```
Apply execution configurations and run:
```bash
chmod +x check_user.sh
./check_user.sh
```
* **Expected Output (Unprivileged Mode):** `Running as [your username].`

#### Subtask 2.3: Use a `for` Loop
Create an iterative script block to handle sequential batch routines:
```bash
nano loop.sh
```
Append the loop block to count from 1 to 5:
```bash
#!/bin/bash
for i in {1..5}; do
  echo "Number: \$i"
done
```
Apply execution properties and run:
```bash
chmod +x loop.sh
./loop.sh
```
* **Expected Output:**
  ```text
  Number: 1
  Number: 2
  ...
  Number: 5
  ```

---

### Task 3: Debugging Shell Scripts

#### Subtask 3.1: Debug with `-x`
Analyze script actions step-by-step to trace how variables expand and watch execution paths live:
```bash
bash -x hello_world.sh
```
* **Expected Output Structure:**
  ```text
  + echo 'Hello, World!'
  Hello, World!
  ```
> 💡 lines prefixed with `+` expose the exact internal command string being processed before printing results.

#### Subtask 3.2: Handle Errors
1. Break `hello_world.sh` by removing or misspelling the shebang declaration header.
2. Execute `./hello_world.sh` to see how the local terminal drops execution or parses incorrectly.
3. Repair the first line, then re-test to confirm functionality drops back into its normal baseline parameters.

---

## 🔬 Skills Verification
Verify all project code blocks compiled during this lab exist with correct properties in your tracking path:
```bash
ls -l ~/shell_scripts
```

## 🏁 Conclusion
By completing this automation lab, you have mastered:
* Structuring executable scripts with correct shebang paths.
* Storing and querying variables dynamically inside processing streams.
* Constructing basic conditionals and counting structures.
* Tracing logic variables using verbose execution modes (`-x`).

These core scripting competencies provide the foundational framework needed to automate repetitive administration chores, map infrastructure, and manage container platforms like **Red Hat OpenShift**.

## 🚀 Next Steps
* Expand your scripts to handle external user inputs using arguments (`$1`, `$2`) or read parameters dynamically via `read`.
* Explore structural script encapsulation using custom reusable functions.
