# Processing Input in Shell Scripts

This repository contains a comprehensive guide to building interactive Bash automation tools. You will master runtime data ingestion using positional arguments, manage live execution variables using terminal prompts, and construct bulletproof logic pipelines using fail-safe error handles.

## 🎯 Objectives
By the end of this lab, you will be able to:
* **Ingest Command-Line Arguments:** Use native positional parameter matrices (`$1`, `$2`, etc.) to pass raw parameters to scripts instantly.
* **Parse Live User Input:** Modify running script workflows on the fly using interactive text prompts.
* **Isolate Processing Anomalies:** Intercept invalid inputs, log errors to standard error (`stderr`), and enforce correct return exit codes.
* **Harden Operational Logic:** Utilize protective structural flags (like `set -e`) to stop scripts immediately if errors are detected.

## 📋 Prerequisites
* **OS:** Any modern Linux-based environment (e.g., Fedora, Ubuntu, CentOS, RHEL).
* **Skills:** Functional understanding of basic loops, variable management, and filesystem navigation.
* **Utilities:** Terminal console entry paired with a standard terminal-based text editor (`nano`, `vim`).

---

## 🛠️ Step-by-Step Implementation

### Task 1: Using Positional Parameters

#### Subtask 1.1: Create a Script with Positional Parameters
Open a terminal shell session and open a new configuration script path:
```bash
nano input_script.sh
```
Append the script code block below to track incoming command arguments:
```bash
#!/bin/bash
echo "First argument: $1"
echo "Second argument: $2"
echo "All arguments: $@"
echo "Total arguments: $#"
```
Save your workspace file (`Ctrl+O`, `Enter`), terminate the editor window (`Ctrl+X`), and make the text file executable:
```bash
chmod +x input_script.sh
```

#### Subtask 1.2: Execute the Script with Arguments
Test run the newly compiled variable processor by appending sample strings:
```bash
./input_script.sh apple banana cherry
```
* **Expected Output:**
  ```text
  First argument: apple
  Second argument: banana
  All arguments: apple banana cherry
  Total arguments: 3
  ```

> 💡 **Core Ingestion Reference:**
> * `$1`, `$2`, ... `$N` map to the discrete ordered string values passed after the script call.
> * `$@` evaluates to a collection holding **all** incoming parameter items.
> * `$#` tracks the total **count** integer representing overall parameters submitted.

---

### Task 2: Parsing User Input

#### Subtask 2.1: Read Input During Execution
Expand your script file to ask for fallback user credentials interactively if command arguments are missing:
```bash
#!/bin/bash
read -p "Enter your name: " name
echo "Hello, \(name! You provided \)# arguments."
```
Execute the task cleanly from your terminal:
```bash
./input_script.sh
```
* **Expected Outcome:** The processing line pauses, asks for input strings using a custom prompt message, and displays a personal greeting layout on your screen.

#### Subtask 2.2: Modify Behavior Based on Input
Update your execution code to change paths on the fly. The script will look for an explicit inline argument; if none is found, it will gracefully open an input prompt instead:
```bash
#!/bin/bash
if [ \$# -eq 0 ]; then
  read -p "Enter a directory path: " path
else
  path=\$1
fi
ls -l \$path
```
Evaluate both workflow scenarios to ensure routing behaves correctly:
```bash
# Workflow A: Processes inline position target directly
./input_script.sh /tmp

# Workflow B: Automatically drops back to open input prompts
./input_script.sh
```
* **Troubleshooting Tip:** Protect string checks from crashing if users accidentally press `Enter` without typing content by checking for empty strings with `-z "$path"`.

---

### Task 3: Graceful Error Handling

#### Subtask 3.1: Validate Input
Harden the directory scanner script by embedding explicit resource-existence validation logic (`-d` checks if directories are valid):
```bash
#!/bin/bash
if [ \$# -eq 0 ]; then
  read -p "Enter a directory path: " path
else
  path=\$1
fi

if [ ! -d "\$path" ]; then
  echo "Error: \$path is not a valid directory." >&2
  exit 1
fi
ls -l \$path
```
* **Expected Behavior:** Passing an invalid target string instantly short-circuits the pipeline, drops an descriptive alert message directly into the system error log stream, and reports an operational exit failure code of `1`.

#### Subtask 3.2: Use `set -e` for Automatic Error Handling
Inject a strict error handling flag onto the header tracking section of your code blocks to force instant processing self-termination if any step crashes out:
```bash
#!/bin/bash
set -e
[ -z "\$1" ] && read -p "Enter a number: " num || num=\$1
echo "Result: \$((num * 2))"
```
* **Verification Test:** Try feeding broken alphanumeric letters (e.g., `xyz`) instead of clean integers. The math evaluation module will trigger a error and immediately halt further script execution.

> 💡 **Key Concept:** Applying structural indicators like `>&2` routes text notifications straight into standard error streams (`stderr`). Returning non-zero status metrics (`exit 1`) tells modern parent automation layers that a script layout failed.

---

## 🏁 Conclusion
By completing these advanced parameter ingestion tasks, you have mastered:
* Consuming variable parameters via positional metrics (`$1`, `$#`, `$@`).
* Gathering user-defined parameters on the fly via the `read` shell utility.
* Hardening automation script stability via standard validation statements and error stream segregation (`>&2`).
* Enforcing system-wide structural integrity using automated execution brakes (`set -e`).

Constructing stable user ingestion scripts provides a vital toolset needed to develop flexible management tools, configure container initialization blocks, and manage platform deployments inside ecosystems like **Red Hat OpenShift**.

## 🚀 Next Steps
* Experiment with compiling mature custom utility options using native shell option parsing blocks (`getopts` to handle flags like `-f`, `--file`).
* Combine positional arguments with fallback prompts to build dynamic administration scripts.
