# 🖥️ Identifying and Killing CPU/Memory Intensive Processes

## 🎯 Objectives
By the end of this lab, you will be able to:
* 📊 Monitor system processes using `top` and `ps` commands.
* 🔍 Identify processes consuming excessive CPU or memory resources.
* 🛑 Terminate unresponsive or resource-intensive processes using `kill` and `killall`.
* ⚖️ Adjust process priorities using `nice` and `renice`.
* 🐧 Understand core process management concepts in Linux systems.

## 📋 Prerequisites
* **Operating System:** A Linux system (RHEL, CentOS, Fedora, or Ubuntu).
* **Skills:** Basic command-line familiarity.
* **Privileges:** `sudo` or root privileges for process termination and priority adjustment.

---

## 🛠️ Lab Tasks

### 📂 Task 1: Monitoring Processes with top and ps

#### ⚙️ Subtask 1.1: Using the top command
Open a terminal and run the interactive monitoring tool:
```bash
top
```
Observe the real-time system summary interface:
* **CPU usage:** `us` (user), `sy` (system), `ni` (nice), `id` (idle).
* **Memory usage:** Quantities for total, free, used, and buff/cache.
* **Process list:** Sorted automatically by CPU usage by default.

**Interactive Hotkeys inside top:**
* Press `M` to sort the process list by memory usage.
* Press `P` to return to sorting by CPU usage.
* Press `q` to exit the interface.

#### ⚙️ Subtask 1.2: Using ps for process analysis
* **List all running processes with extended CPU and memory details:**
  ```bash
  ps aux
  ```
* **Filter and display the top 5 CPU-consuming processes:**
  ```bash
  ps aux --sort=-%cpu | head -6
  ```
* **Filter and display the top 5 memory-consuming processes:**
  ```bash
  ps aux --sort=-%mem | head -6
  ```
* **Expected Outcome:** A structured static listing showing the PID, CPU%, MEM%, and command path details.

> 💡 **Troubleshooting Tip:** If `ps` shows truncated or incomplete text output, widen your terminal window or pipe the stream into the `less` pager:
> ```bash
> ps aux | less
> ```

---

### 📂 Task 2: Terminating Processes

#### ⚙️ Subtask 2.1: Graceful termination with kill
Identify the targeted process ID (PID) using `pidof` or `pgrep`:
```bash
pidof firefox
# OR
pgrep -l firefox
```
Send a standard `SIGTERM` (15) signal to prompt a graceful cleanup and shutdown:
```bash
kill <PID>
```
Verify the process status to confirm closure:
```bash
ps -p <PID>
```

#### ⚙️ Subtask 2.2: Forceful termination
If a program crashes and fails to respond to `SIGTERM`, force execution termination using a `SIGKILL` (9) signal. Note that `SIGKILL` cannot be blocked or ignored by the process:
```bash
kill -9 <PID>
```

#### ⚙️ Subtask 2.3: Using killall
* **Terminate all application instances by binary name gracefully:**
  ```bash
  killall chrome
  ```
* **Force-terminate all application instances by binary name:**
  ```bash
  killall -9 chrome
  ```

> ⚠️ **Warning:** Exercise high caution when running `kill -9` and `killall`. Forcing termination skips file savings and can cause sudden data loss or system instability.

---

### 📂 Task 3: Process Priority Adjustment

#### ⚙️ Subtask 3.1: Launching processes with nice
Launch a new process with an adjusted priority. Applying a higher nice value reduces its execution urgency:
```bash
nice -n 19 tar -czf backup.tar.gz /large_directory
```
*Note: Nice values span from `-20` (highest execution priority) to `19` (lowest execution priority).*

#### ⚙️ Subtask 3.2: Adjusting running processes with renice
1. Find a running, resource-intensive target process via `top`.
2. Document its **PID** and current nice status inside the **NI** column.
3. Reprioritize the live task using `renice`:
   ```bash
   sudo renice -n 10 -p <PID>
   ```
4. Verify the updated priority value within the `top` overview panel.

> 🔒 **Note:** Only the root user or accounts using `sudo` can elevate process priority (assigning lower nice values) on existing tasks.

---

## 🏁 Conclusion
You have completed the fundamental process management exercises:
* Monitoring dynamic resource statistics via `top` and `ps`.
* Tracking down high-consumption resource drains.
* Executing controlled or forced process termination routines.
* Altering scheduler values to optimize system performance bounds.

These system skills form the foundation for maintaining underlying performance, troubleshooting environments, and managing containerized applications like OpenShift.

### 🚀 Additional Exercises
* Create an automated shell script that tracks, isolates, and logs the top 3 CPU-intensive processes into a file every minute.
* Explore resource limits at the kernel level utilizing Linux `cgroups`.
* Configure structural `systemd` service files containing fixed CPU/memory constraints.

### 📚 References
* Manual pages: `man top`, `man ps`, `man kill`, `man nice`
* Red Hat System Administration documentation guidelines
* Linux Performance Analysis methodologies
