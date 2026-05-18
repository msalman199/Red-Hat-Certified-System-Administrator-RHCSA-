
# 🖥️ Operating Running Systems

## 🎯 Objectives
By the end of this lab, you will be able to:
* 🔄 Reboot, shut down, and manage system power states.
* 📊 Monitor system processes and resource usage using `top`, `ps`, and `htop`.
* 🛑 Identify and terminate unneeded or misbehaving processes.

## 📋 Prerequisites
* 🐧 A Linux-based system (Ubuntu/CentOS/Fedora recommended).
* 🔑 Terminal access with `sudo` privileges.
* 💻 Basic familiarity with Linux command-line operations.

---

## 🛠️ Task 1: Managing System Power States

### ⚙️ Subtask 1.1: Rebooting the System
* **Command:** `sudo reboot`
* **Explanation:** Safely restarts the system. Requires `sudo` privileges.
* **Expected Outcome:** The system initiates a reboot sequence.
* **Troubleshooting:** If the command fails, verify privileges using `sudo -l`.

### ⚙️ Subtask 1.2: Shutting Down the System
* **Command:** `sudo shutdown -h now`
* **Explanation:** Halts the system immediately. You can also use `sudo poweroff`.
* **Expected Outcome:** The system powers off.

### ⚙️ Subtask 1.3: Scheduling a Shutdown
* **Command:** `sudo shutdown -h +10 "System will shut down in 10 minutes"`
* **Explanation:** Schedules a shutdown in 10 minutes and broadcasts a message to all logged-in users.
* **Expected Outcome:** A notification appears, and the system shuts down after 10 minutes.

---

## 🔍 Task 2: Monitoring System Processes

### ⚙️ Subtask 2.1: Using top for Real-Time Monitoring
* **Command:** `top`
* **Explanation:** Displays real-time system processes, CPU, and memory usage. Press `q` to exit.
* **Key Metrics:** `%CPU` (CPU usage per process) and `%MEM` (Memory usage per process).
* **Expected Outcome:** A dynamic list of running processes appears.

### ⚙️ Subtask 2.2: Using ps to List Processes
* **Command:** `ps aux`
* **Explanation:** Lists all running processes with extended details (user, PID, CPU, memory, command).
* **Expected Outcome:** A static list of processes is displayed.

### ⚙️ Subtask 2.3: Using htop for Enhanced Monitoring
* **Installation:**
  ```bash
  sudo apt install htop       # Ubuntu/Debian  
  sudo dnf install htop      # Fedora/CentOS  
  ```
* **Command:** `htop`
* **Explanation:** Interactive process viewer with color-coded metrics. Supports sorting, filtering, and process management.
* **Expected Outcome:** A detailed and interactive process list appears.

---

## ❌ Task 3: Terminating Processes

### ⚙️ Subtask 3.1: Finding a Process by Name
* **Command:** `pgrep -l firefox`
* **Explanation:** Finds the Process ID (PID) of a running application (e.g., Firefox).
* **Expected Outcome:** Outputs the PID of the process (e.g., `1234 firefox`).

### ⚙️ Subtask 3.2: Killing a Process Using kill
* **Command:** `kill -9 1234`
* **Explanation:** Sends a `SIGKILL` signal, forcing the process to terminate. Replace `1234` with the actual PID.
* **Expected Outcome:** The specified process terminates.

### ⚙️ Subtask 3.3: Using pkill to Terminate by Name
* **Command:** `pkill -9 firefox`
* **Explanation:** Kills all processes matching the name "firefox."
* **Expected Outcome:** All instances of Firefox are terminated.

---

## 🏁 Conclusion
This lab covers essential skills for system administration and troubleshooting in Linux environments, including:
* Managing system power states (`reboot`, `shutdown`).
* Monitoring processes (`top`, `ps`, `htop`).
* Terminating misbehaving processes (`kill`, `pkill`).

### 💡 Troubleshooting Tips
* If a process does not terminate, verify its PID using `ps aux | grep <process_name>`.
* Use `killall` as an alternative to `pkill` for terminating multiple instances.

### 🚀 Next Steps
* Explore `systemd` for advanced service management (`systemctl`).
* Learn about process priorities (`nice`, `renice`).
