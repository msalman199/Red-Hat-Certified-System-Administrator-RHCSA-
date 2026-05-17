# Using grep and Regular Expressions

This repository provides a practical, hands-on guide to mastering text pattern matching, advanced regular expressions (regex), and system log filtering using the Linux `grep` utility.

## 🎯 Objectives
By the end of this lab, you will be able to:
* **Scan Files Efficiently:** Use `grep` to quickly find specific text patterns inside files.
* **Apply Regex Logic:** Implement Basic Regular Expressions (BRE) and Extended Regular Expressions (ERE).
* **Parse System Logs:** Filter and analyze production log files using advanced search patterns.
* **Fine-Tune Searches:** Utilize essential `grep` modifiers to customize output results.

## 📋 Prerequisites
* **OS:** Any Linux-based operating system (e.g., Ubuntu, Fedora, CentOS, RHEL).
* **Environment:** Access to a terminal shell instance.
* **Utilities:** Standard GNU utilities and a basic command-line text editor (`nano`, `vim`).

---

## 🛠️ Step-by-Step Implementation

### Task 1: Basic grep Usage

#### Subtask 1.1: Simple Text Search
First, generate a baseline sample file containing a clean list of strings:
```bash
echo -e "apple\nbanana\ncherry\ndate\nelderberry\nfig\ngrape" > sample.txt
```
Execute a literal string match query against the document:
```bash
grep "banana" sample.txt
```
* **Expected Output:** `banana`

#### Subtask 1.2: Case-Insensitive Search
By default, `grep` is strictly case-sensitive. Force the matching engine to ignore character casing using the `-i` flag:
```bash
grep -i "Apple" sample.txt
```
* **Expected Output:** `apple`

#### Subtask 1.3: Count Matching Lines
Instead of printing the actual text lines, isolate and count the number of matching records using the `-c` modifier flag:
```bash
grep -c "a" sample.txt
```
* **Expected Output:** An integer showing the total line count (e.g., `4`).

---

### Task 2: Regular Expressions with grep

#### Subtask 2.1: Basic Regex Patterns
Anchor your search patterns to target structural positioning within lines.

##### 🔹 Line-Start Anchor (`^`)
Isolate rows that begin strictly with the letter "a":
```bash
grep "^a" sample.txt
```
* **Expected Output:** `apple`

##### 🔹 Line-End Anchor (`$`)
Isolate rows that terminate strictly with the letter "e":
```bash
grep "e$" sample.txt
```
* **Expected Output:**
  ```text
  apple
  date
  grape
  ```

#### Subtask 2.2: Character Classes
Use brackets (`[...]`) to form sets of permitted matching characters. Search for any standard lowercase vowel positioned directly before the letter "p":
```bash
grep "[aeiou]p" sample.txt
```
* **Expected Output:**
  ```text
  apple
  grape
  ```

#### Subtask 2.3: Quantifiers
Use Extended Regular Expressions (`-E` or `egrep`) to define precise repetition limits using curly brackets (`{min,max}`). Scan for lines containing two or more vowels appearing consecutively:
```bash
grep -E "[aeiou]{2,}" sample.txt
```
* **Expected Output:**
  ```text
  banana
  elderberry
  ```

---

### Task 3: Searching Log Files

#### Subtask 3.1: Filter Log Entries
Isolate core problems inside large files by cloning system registries over to a safe testing zone:
```bash
sudo cp /var/log/syslog /tmp/syslog_sample
```
Filter out all operational anomalies by searching case-insensitively for anomalies or tracking tags:
```bash
grep -i "error" /tmp/syslog_sample
```
* **Expected Output:** A dynamic terminal printout listing every raw system line containing the word "error".

#### Subtask 3.2: Extract Timestamps
Parse log lines chronologically by scanning for standard timestamp layouts at the start of entries (e.g., matching a three-letter month followed by a two-digit day):
```bash
grep -E "^[A-Za-z]{3} [0-9]{2}" /tmp/syslog_sample
```
* **Expected Output:** Log lines filtered to display only those initiating with structured date headers.

---

## 💡 Troubleshooting Tips
* **Empty Returns:** If a query yields blank lines, check your path arguments or verify character casing rules against the target file.
* **Regex Errors:** If advanced patterns are failing or printing literally, make sure you enabled the Extended engine via `grep -E`.
* **Testing Platform:** For complex expression logic development, validate your query layout patterns interactively using tools like [regex101.com](https://regex101.com).

## 🏁 Conclusion
By executing this lab layout, you have mastered:
* Basic and advanced string processing mechanics using `grep`.
* Designing reusable, high-efficiency regex logic patterns.
* Parsing structural data from production application log trees.

To continue practicing your skills, look deeper into local systems paths via `/var/log/` or read through manual parameters using `man grep`.
