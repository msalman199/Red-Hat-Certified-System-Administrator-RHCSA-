# Using Loops in Shell Scripts

This repository contains a comprehensive guide to understanding and implementing iteration mechanics, conditional repetition loops, and flow control overrides inside Bash shell scripts.

## 🎯 Objectives
By the end of this lab, you will be able to:
* **Automate Batch Processing:** Write `for` loops to iterate over explicit item collections, dynamic directory globs, and external arguments.
* **Orchestrate State-Driven Loops:** Build `while` and `until` repetition workflows based on boolean evaluations and counter changes.
* **Inject Logic into Iterations:** Nest `if` statements inside looping routines to create robust data-filtering logic.
* **Override Execution Paths:** Safely modify structural loop states using explicit execution brakes (`break`) and skip indicators (`continue`).

## 📋 Prerequisites
* **OS:** Any modern Linux-based environment (e.g., Fedora, Ubuntu, CentOS, RHEL) running a standard Bash interpreter.
* **Skills:** Comfort with fundamental scripting components (variables, basic permission management, conditional statement logic).
* **Utilities:** Access to an interactive terminal console paired with a text editor (`nano`, `vim`).

---

## 🛠️ Step-by-Step Implementation

### Task 1: Writing for Loops

#### Subtask 1.1: Basic `for` Loop Syntax
Open your active terminal workspace and initialize a new automation file to explore item parsing:
```bash
nano for_script.sh
```
Append the following structured array processing script:
```bash
#!/bin/bash
echo "Basic for loop example:"
for fruit in apple banana orange; do
    echo "I like $fruit"
done
```
Save your work (`Ctrl+O`, `Enter`) and exit out of the editing window (`Ctrl+X`). Elevate permissions to make the text block executable, then test run:
```bash
chmod +x for_script.sh
./for_script.sh
```
* **Expected Output:**
  ```text
  Basic for loop example:
  I like apple
  I like banana
  I like orange
  ```

#### Subtask 1.2: Processing Files with `for`
Automate administrative cleanup or indexing tasks by driving loop iterations directly through filesystem globs:
```bash
nano file_loop.sh
```
Append the script code below to search the active directory path dynamically:
```bash
#!/bin/bash
echo "List of .txt files:"
for file in *.txt; do
    echo "Found file: $file"
done
```
Apply execution properties and run:
```bash
chmod +x file_loop.sh
./file_loop.sh
```
* **Expected Output:** Console displays path indexes for every matching `.txt` document inside the execution folder.

---

### Task 2: Using while and until Loops

#### Subtask 2.1: `while` Loop for Conditional Repetition
Execute automated sequences repeatedly as long as a baseline validation rule evaluates to true:
```bash
nano while_script.sh
```
Append the sequential numeric incremental calculation script block:
```bash
#!/bin/bash
count=1
while [ $count -le 5 ]; do
    echo "Count: $count"
    ((count++))
done
```
Set execution parameters live on your system and run:
```bash
chmod +x while_script.sh
./while_script.sh
```
* **Expected Output:** Counters increment sequentially from `1` through `5`.

#### Subtask 2.2: `until` Loop for Reverse Logic
Execute automated workflows repeatedly until a designated event occurs (useful for loop setups waiting on network state changes):
```bash
nano until_script.sh
```
Append the following logic block to run a reverse countdown:
```bash
#!/bin/bash
count=3
until [ $count -eq 0 ]; do
    echo "Countdown: $count"
    ((count--))
done
echo "Done!"
```
Apply execution properties and evaluate:
```bash
chmod +x until_script.sh
./until_script.sh
```
* **Expected Output:**
  ```text
  Countdown: 3
  Countdown: 2
  Countdown: 1
  Done!
  ```

---

### Task 3: Combining Loops with Conditionals

#### Subtask 3.1: Filtering Files with Loops and `if`
Isolate specific targets out of large file paths by nesting security filter conditions directly inside a loop matrix:
```bash
nano filter_files.sh
```
Append the code block below to evaluate the read permissions status (`-r`) of files:
```bash
#!/bin/bash
for file in *; do
    if [ -r "$file" ]; then
        echo "Readable file: $file"
    fi
done
```
Elevate script properties and run:
```bash
chmod +x filter_files.sh
./filter_files.sh
```
* **Expected Output:** Lists files from the current folder directory that match your profile's security permission rights.

#### Subtask 3.2: Loop Control with `break` and `continue`
Halt heavy loop processing immediately upon meeting a precise matching value boundary condition:
```bash
nano control_loop.sh
```
Append the short-circuit logic script:
```bash
#!/bin/bash
for num in {1..10}; do
    if [ $num -eq 5 ]; then
        break
    fi
    echo "Number: $num"
done
echo "Loop exited at 5"
```
Apply execution properties and run:
```bash
chmod +x control_loop.sh
./control_loop.sh
```
* **Expected Output:**
  ```text
  Number: 1
  Number: 2
  Number: 3
  Number: 4
  Loop exited at 5
  ```

---

## 💡 Troubleshooting Tips

* **🚫 Permission Denied:** Ensure that you elevated script execution rights via the `chmod +x script_name.sh` terminal wrapper before executing.
* **⚠️ Hidden Syntax Anomalies:** Run an internal logic compilation check on your script to map missing bracket tokens or structure errors without firing commands: `bash -n script_name.sh`.
* **🔄 Infinite Loop Breaks:** If an increment statement failure traps your terminal shell inside an unending processing cycle, terminate the active thread instantly by pressing `Ctrl + C`.

## 🏁 Conclusion
By executing these advanced automation patterns, you have mastered:
* Leveraging `for` loops to handle file groupings and static string structures efficiently.
* Designing state-driven logic structures using `while` and `until` blocks.
* Nesting permission filters and loop controls to execute precise automation paths.

These automated iteration structures form the core foundation needed to design custom health monitoring daemons, build cron automation jobs, and process continuous telemetry data streams within environments like **Red Hat OpenShift**.

## 🚀 Next Steps
* Experiment with nesting complex multi-level loops to process tabular matrix sheets.
* Scale data handling speeds by passing elements dynamically via Bash system arrays.
