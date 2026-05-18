# 🖥️ Adjusting Process Scheduling

## 🎯 Objectives
By the end of this lab, you will be able to:
* ⚖️ Modify process priorities using `nice` and `renice`.
* 📊 Monitor and optimize process performance using `top` and `htop`.
* 🧠 Understand process states and dynamically adjust system scheduling.

## 📋 Prerequisites
* 🐧 A Linux-based system (Ubuntu, CentOS, RHEL, or Fedora).
* 💻 Basic familiarity with the Linux command line.
* 🔑 Administrative (`sudo`) privileges for priority adjustments.
* 📦 Installation of `htop` (if not pre-installed).

---

## 🛠️ Lab Tasks

### 📂 Task 1: Changing Process Priority Using nice and renice

#### ⚙️ Subtask 1.1: Launch a Test Process
Open your terminal and run a CPU-intensive command in the background to simulate work:
```bash
sha1sum /dev/zero &
```
* **Expected Outcome:** The process starts running in the background, and its unique Process ID (PID) is displayed in the terminal.

#### ⚙️ Subtask 1.2: Check Default Priority
Use the `ps` command to inspect the default scheduler nice value (`NI`) of the background process:
```bash
ps -l -p \$(pgrep sha1sum)
```
* **Expected Outcome:** The `NI` column shows a value of `0`, which indicates the standard default priority level.

#### ⚙️ Subtask 1.3: Adjust Priority Using nice
Launch a secondary instance of the command with a modified priority level using the `-n` flag:
```bash
nice -n 10 sha1sum /dev/zero &
```
* **Explanation:** Higher nice values yield CPU time to other tasks. Setting it to `10` lowers its execution priority.
* **Verification:** Run the following command to check the priority of the newest instance:
  ```bash
  ps -l -p \$(pgrep sha1sum | tail -1)
  ```
* **Expected Outcome:** The output shows an `NI` value of `10`.

#### ⚙️ Subtask 1.4: Adjust Priority of a Running Process Using renice
Dynamically adjust the priority of your first running background process:
```bash
sudo renice -n 5 -p \$(pgrep sha1sum | head -1)
```
* **Explanation:** The `-n 5` flag reconfigures the process to a higher priority than 10, but a lower priority than its original default of 0.
* **Verification:** Confirm the runtime modification:
  ```bash
  ps -l -p \$(pgrep sha1sum | head -1)
  ```
* **Expected Outcome:** The value under the `NI` column updates directly to `5`.

---

### 📂 Task 2: Monitoring Processes with top and htop

#### ⚙️ Subtask 2.1: Use top to View Process Stats
Launch the built-in system monitor:
```bash
top
```
* **Key Observations:** Locate the `PR` (Priority) and `NI` (Nice) columns to observe process distribution and CPU metrics.
* **Navigation:** Press `q` to safely exit the dashboard.

#### ⚙️ Subtask 2.2: Install and Use htop
If `htop` is not available on your system, install it using your distribution package manager:
```bash
sudo apt install htop       # Debian/Ubuntu  
sudo dnf install htop       # RHEL/CentOS/Fedora  
```
Launch the interactive process viewer:
```bash
htop
```
* **Key Features:** Provides color-coded meters for CPU/Memory, an organized parent-child process tree view, and live priority tuning utilizing the `F7` (increase nice) and `F8` (decrease nice) hotkeys.
* **Navigation:** Press `F10` to exit.

---

### 📂 Task 3: Understanding Process States and Dynamic Adjustments

#### ⚙️ Subtask 3.1: Identify Process States
List active processes alongside their execution states:
```bash
ps aux
```
*Note: Key state indicators include `R` (Running), `S` (Interruptible Sleeping), and `D` (Uninterruptible Disk Sleep).*

#### ⚙️ Subtask 3.2: Kill a Low-Priority Process
Terminate the active instances of our test background process:
```bash
kill \$(pgrep sha1sum)
```

#### ⚙️ Subtask 3.3: Adjust Scheduling Policy (Optional)
Use the `chrt` command to manipulate real-time system scheduling characteristics (requires administrative root access):
```bash
sudo chrt -f -p 99 \$(pgrep sha1sum)
```
* **Explanation:** The `-f` option forces the kernel scheduler to handle the task using a First-In-First-Out (`FIFO`) processing structure at a real-time priority level of `99`.

---

## 🏁 Conclusion
By finishing this lab session, you have mastered:
* Modifying scheduler weight metrics using `nice` and live application tracking with `renice`.
* Reading process indicators and behavior states through `top` and `htop`.
* Setting real-time real-world core processor behaviors using `chrt`.

### 💡 Troubleshooting Tips
* If a `renice` instruction fails, double-check that your command is preceded by `sudo`.
* For stubborn or frozen tasks that ignore clean termination instructions, use a forceful termination override: `kill -9 <PID>`.
* Confirm your system tracking tool installation status using the shell check tool: `which htop`.

### 📚 Further Reading
* System Manual Pages: `man nice`, `man renice`, `man chrt`
* Linux Architecture Documentation: Linux Process Scheduling Frameworks
