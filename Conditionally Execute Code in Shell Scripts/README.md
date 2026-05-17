# Conditionally Execute Code in Shell Scripts

This repository contains a hands-on guide to mastering conditional logic, boolean validation checks, and decision-making structures inside Bash shell scripts.

## 🎯 Objectives
By the end of this lab, you will be able to:
* **Orchestrate Logical Branches:** Implement complex multi-tier conditional routing with `if`, `elif`, and `else` statements.
* **Audit Filesystem Objects:** Perform dynamic system validation checks on files and directories using terminal operators.
* **Validate String Content:** Securely evaluate and compare text input variables using exact matching boundaries.
* **Deconstruct Syntax Handles:** Contrast the classic `test` processing engine against the preferred bracket `[ ]` wrapper design syntax.

## 📋 Prerequisites
* **OS:** Any modern Linux-based environment (e.g., Fedora, Ubuntu, CentOS, RHEL).
* **Skills:** Functional understanding of basic scripting basics (shebangs, variable storage, permissions expansion).
* **Utilities:** Terminal execution space loaded with a standard console text editor (`nano`, `vim`).

---

## 🛠️ Step-by-Step Implementation

### Task 1: Using if, elif, and else for Conditional Execution

#### Subtask 1.1: Basic `if` Statement
Open your active shell session window and spin up a new automation script skeleton:
```bash
nano basic_if.sh
```
Append the conditional numeric checking logic block below:
```bash
#!/bin/bash
read -p "Enter a number: " num
if [ $num -gt 10 ]; then
    echo "The number is greater than 10."
fi
```
Save the workspace asset (`Ctrl+O`, `Enter`) and exit the editor (`Ctrl+X`). Elevate the target permissions layout bit to declare it an active program element, then test execute:
```bash
chmod +x basic_if.sh
./basic_if.sh
```
* **Expected Output Validation:** Inputting value `15` prints out `"The number is greater than 10."` into your terminal window stream. Passing lesser items completes execution silently.

#### Subtask 1.2: Using `elif` and `else`
To process multiple variant conditions along with fallback parameters, expand your logic branches by designing a nested validation workflow file:
```bash
nano if_elif_else.sh
```
Append the following structured comparison script block:
```bash
#!/bin/bash
read -p "Enter a number: " num
if [ $num -gt 10 ]; then
    echo "Greater than 10."
elif [ $num -eq 10 ]; then
    echo "Equal to 10."
else
    echo "Less than 10."
fi
```
Apply execution properties and run evaluations across matching variable constraints:
```bash
chmod +x if_elif_else.sh
./if_elif_else.sh
```
* **Expected Test Verification:**
  * Passing value `12` returns \(\rightarrow\) `Greater than 10.`
  * Passing value `10` returns \(\rightarrow\) `Equal to 10.`
  * Passing value `5` returns \(\rightarrow\) `Less than 10.`

---

### Task 2: Performing Tests (File Checks, String Comparisons)

#### Subtask 2.1: File Existence Check
Automate asset tracking loops by using built-in system checking operators (like `-f` for verifying regular file assets):
```bash
nano file_check.sh
```
Append the following verification path script string:
```bash
#!/bin/bash
if [ -f "/etc/passwd" ]; then
    echo "File /etc/passwd exists."
else
    echo "File not found."
fi
```
Lock modifications into disk and test the script execution path:
```bash
chmod +x file_check.sh
./file_check.sh
```
* **Expected Output:** `File /etc/passwd exists.`

#### Subtask 2.2: String Comparison
Create an interactive script profile to evaluate text configurations and user inputs precisely:
```bash
nano string_compare.sh
```
Add the case handling selection logic below:
```bash
#!/bin/bash
read -p "Enter 'yes' or 'no': " answer
if [ "$answer" = "yes" ]; then
    echo "You agreed."
elif [ "$answer" = "no" ]; then
    echo "You disagreed."
else
    echo "Invalid input."
fi
```
Set execution parameters live on the filesystem:
```bash
chmod +x string_compare.sh
./string_compare.sh
```
* **Expected Test Verification:**
  * Input string `yes` returns \(\rightarrow\) `You agreed.`
  * Input string `no` returns \(\rightarrow\) `You disagreed.`
  * Input string `maybe` returns \(\rightarrow\) `Invalid input.`

---

### Task 3: Using [ ] vs. test Commands

#### Subtask 3.1: Using `test` Command
The shell interprets data checks natively via the core binary tool `test`. Build a script tracking framework to witness this interface pattern:
```bash
nano test_command.sh
```
Append the following numeric bounds check code:
```bash
#!/bin/bash
read -p "Enter a number: " num
if test $num -lt 5; then
    echo "Number is less than 5."
else
    echo "Number is 5 or greater."
fi
```
Elevate execution tracking properties and evaluate:
```bash
chmod +x test_command.sh
./test_command.sh
```
* **Expected Test Verification:** Input string `3` triggers the lower loop boundary statement, while passing value `7` drops down onto the alternative branch condition block.

#### Subtask 3.2: Using `[ ]` (Preferred Syntax)
Modify the system script above to exchange the verbose `test` declaration for standard clean spacing block brackets:
```bash
#!/bin/bash
read -p "Enter a number: " num
if [ $num -lt 5 ]; then
    echo "Number is less than 5."
else
    echo "Number is 5 or greater."
fi
```
> 💡 **Architectural Note:** The bracket configuration `[ ]` is functionally equivalent to triggering the legacy `test` engine under the hood. However, it is the standard preferred syntax across enterprise automation repositories because it mimics human readability rules found in structured software languages.

---

## 💡 Troubleshooting Tips

* **⚠️ Error Block `[: missing ]`:** Bash handles the left-bracket `[` as a literal command call name. You must explicitly separate arguments with clean terminal whitespace framing rules (e.g., use `[ $var -eq 5 ]` instead of structural failures like `[$var-eq5]`).
* **⚠️ Error Block `"unary operator expected"`:** If an unexpected evaluation query drops a blank tracking token placeholder into an unquoted processing field, string engines crash out. Safeguard your execution logic against missing data frames by wrapping terminal variables in double-quotes: `[ "$var" = "value" ]`.

## 🏁 Conclusion
By executing this advanced structural logic lab path, you have mastered:
* Handling conditional operational paths via nested `if-elif-else` code loops.
* Auditing physical deployment records using system storage indicators.
* Securing configuration strings from input stream processing errors.

Building out flexible conditional tracking logic forms a baseline foundational requirement for configuring advanced cluster monitoring tools, automating orchestration routines, and running workloads inside container spaces like **Red Hat OpenShift**.

---

If you want to extend this repository layout, let me know if you would like to **embed visual pipeline logic layout flows using Mermaid maps**, **include logic charts for compound operators** (like `-a` / `-o` or `&&` / `||`), or **add automated test validation script hooks**.
