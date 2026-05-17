# Processing Output of Shell Commands in Scripts

This repository contains a comprehensive guide to mastering command substitution techniques, multi-line variable data capture, pipeline string manipulation, and system telemetry array processing inside Bash shell scripts.

## 🎯 Objectives
By the end of this lab, you will be able to:
* **Capture Command Streams:** Intercept dynamic command execution results using traditional backticks and modern `$()` command substitution blocks.
* **Manage Multi-Line Variables:** Safely isolate and store complex command text matrices within system memory without dropping formatting metrics.
* **Manipulate System Telemetry:** Filter, format, and parse live string data sets using tool combinations (`awk`, `tr`, `grep`).
* **Process Dynamic Arrays:** Convert multi-line output streams into structured Bash native tracking arrays (`readarray`).

## 📋 Prerequisites
* **OS:** A modern Linux-based environment (Fedora, CentOS, or RHEL recommended).
* **Interpreter:** Bash shell version 4.0 or later (required for core array processing functionalities).
* **Utilities:** Access to a terminal session paired with a text editing suite (`vim`, `nano`).

---

## 🛠️ Step-by-Step Implementation

### Task 1: Capturing Command Output

#### Subtask 1.1: Using Backticks
Backticks (\``) represent the legacy standard pattern for triggering command substitutions inside POSIX environments. Execute an inline evaluation block directly within your terminal window:
```bash
echo "Today is `date`"
```
* **Expected Output:** `Today is [current system date and time values]`

Compile a tracking script named `backtick_example.sh` to examine multiline directory capturing:
```bash
nano backtick_example.sh
```
Append the automation block below:
```bash
#!/bin/bash
files=`ls -l`
echo "Files in this directory:"
echo "\$files"
```
Lock modifications into disk, elevate file properties to executable parameters, and run:
```bash
chmod +x backtick_example.sh
./backtick_example.sh
```

#### Subtask 1.2: Using `$()` Syntax
The newer `$()` command substitution syntax replaces legacy backticks across modern code structures. Try this directly inside your open terminal window:
```bash
echo "Current user: \$(whoami)"
```
Compile an automated tracking file named `dollar_parenthesis.sh`:
```bash
nano dollar_parenthesis.sh
```
Append the process pipeline checking script below:
```bash
#!/bin/bash
process_count=\$(ps aux | wc -l)
echo "Number of running processes: \$process_count"
```
Apply execution configurations and test run:
```bash
chmod +x dollar_parenthesis.sh
./dollar_parenthesis.sh
```

> 💡 **Architectural Note:** The `$()` layout is the preferred industry standard because it drastically simplifies nested execution loops, preserves interior escape characters perfectly, and completely eliminates whitespace evaluation errors common with backticks.

---

### Task 2: Storing Command Output in Variables

#### Subtask 2.1: Basic Variable Assignment
Test real-time tracking variable mappings inline inside your active terminal instance:
```bash
current_dir=\$(pwd)
echo "You are in: \$current_dir"
```
Create a dedicated platform information report file named `system_info.sh`:
```bash
#!/bin/bash
kernel_version=\$(uname -r)
hostname=\$(hostname)
echo "System Information:"
echo "Kernel: \$kernel_version"
echo "Hostname: \$hostname"
```

#### Subtask 2.2: Multi-line Output Handling
Create a specialized report file named `multi_line.sh` to capture and stream multiline disk information:
```bash
#!/bin/bash
# Capture and preserve multi-line system outputs
disk_info=\$(df -h)

echo "Disk Usage Information:"
echo "\$disk_info" | grep -v "tmpfs"
```
> ⚠️ **Troubleshooting Tip:** Always wrap your shell variables in double quotes (`"$var"`) during text processing routines. Omitting quotes collapses all newline characters (`\n`) down into a single line of whitespace, scrambling tabular system outputs.

---

### Task 3: Processing Captured Output

#### Subtask 3.1: Filtering Output
Build an automated user analytics script named `process_users.sh` to extract active user data logs:
```bash
#!/bin/bash
# Isolate active system users, parse the layout matrix, and calculate total lines
users=\$(who | awk '{print \$1}')
user_count=\((echo "\)users" | wc -l)

echo "Current Users:"
echo "\$users"
echo "Total users logged in: \$user_count"
```

#### Subtask 3.2: Using Output in Calculations
Build a proactive disk analyzer tool named `disk_check.sh` to run conditional thresholds against the root partition (`/`):
```bash
#!/bin/bash
# Pull root capacity, filter headers via awk, and strip down trailing unit notations
avail_space=\$(df -BG / | awk 'NR==2 {print \$4}' | tr -d 'G')

if [ "\$avail_space" -lt 5 ]; then
    echo "Warning: Only \${avail_space}GB remaining in root!"
else
    echo "Disk space OK: \${avail_space}GB available"
fi
```

#### Subtask 3.3: Advanced Processing with Arrays
For managing dense, multi-line telemetry data structures sequentially, leverage index-safe internal data strings by compiling an array parser script:
```bash
#!/bin/bash
# Capture raw text blocks containing active host networking metrics
ip_lines=\$(ip a | grep 'inet ')

# Stream data arrays directly into an isolated array tracking pool
readarray -t ips <<< "\$ip_lines"

echo "Network Interfaces:"
for ip in "\${ips[@]}"; do
    echo "- \$ip"
```

---

## 🏆 Final Laboratory Challenge
Construct a metrics utility that searches the `/var/log` branch to locate log targets exceeding `1MB` sizing guidelines, sums their structural counts, and sums their combined footprint on the disk pool.

### 📝 Reference Automation Script
```bash
#!/bin/bash
# Target files exceeding sizing, execute counters, and print memory sizes
large_files=\$(find /var/log -type f -size +1M)
count=\((echo "\)large_files" | wc -l)
total_size=\$(du -ch \((echo "\)large_files") | grep total | awk '{print \$1}')

echo "Found \$count large log files"
echo "Total size: \$total_size"
```

---

## 💡 Troubleshooting Tips
* **Blank Calculations:** If numeric comparisons error out with an unexpected character or missing value, ensure your `tr` or `awk` strings are actively wiping non-integer text values (like `G`, `M`, or `%`) out of extracted parameters.
* **Array Index Missing:** Verify that you wrapped data streams properly inside the `<<<` triple-angle arrow format block to feed your multi-line values into the `readarray` processing engine correctly.

## 🏁 Conclusion
By executing this output processing lab track, you have mastered:
* Leveraging command substitutions smoothly via backticks and `$()` components.
* Safeguarding multi-line layout formatting within terminal variable maps.
* Parsing system records on the fly using string-processing streams.
* Constructing robust error checking pipelines for data sets.

These advanced automation habits are essential for monitoring server clusters, parsing container application logs, and building cron scripts inside cloud-native systems like **Red Hat OpenShift**.

## 🚀 Next Steps
* Integrate advanced automation steps into your daily scripts by using text tools like `sed` or `jq` to parse structural JSON formats.
