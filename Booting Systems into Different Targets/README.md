# 🖥️ Booting Systems into Different Targets

## 🎯 Objectives
By the end of this lab, you will be able to:
* 🌐 Understand and configure `systemd` targets.
* 🔄 Boot a Linux system into different runlevels (multi-user, graphical, rescue).
* 🎛️ Switch between targets using the `systemctl` command.
* 🛠️ Troubleshoot common boot and target-switching issues.

## 📋 Prerequisites
* 🐧 A Linux system with `systemd` (e.g., Fedora, RHEL, CentOS, or Ubuntu).
* 🔑 Root or `sudo` privileges.
* 💻 Basic familiarity with the command line.

---

## 🛠️ Task 1: Boot into Multi-User, Graphical, or Rescue Mode

### ⚙️ Subtask 1.1: Check Current Target
* **Steps:** Open a terminal and run the following command to check your current default target:
  ```bash
  systemctl get-default
  ```
* **Expected Outcome:** `graphical.target` (default for desktop systems) or `multi-user.target` (for servers).

### ⚙️ Subtask 1.2: Boot into Multi-User Mode (No GUI)
* **Command:** 
  ```bash
  sudo systemctl isolate multi-user.target
  ```
* **Expected Outcome:** The graphical user interface will exit, and the system switches to a text-based console login.
* **Verification:** Run `systemctl get-default` to confirm the active state has changed.

### ⚙️ Subtask 1.3: Boot into Graphical Mode
* **Command:** 
  ```bash
  sudo systemctl isolate graphical.target
  ```
* **Expected Outcome:** The graphical environment starts up, displaying the desktop environment.

### ⚙️ Subtask 1.4: Boot into Rescue Mode (Emergency Shell)
* **Steps:** 
  1. Reboot the system and interrupt the boot process by pressing `e` in the GRUB menu.
  2. Append `systemd.unit=rescue.target` to the end of the kernel command line.
  3. Press `Ctrl+X` to complete the boot sequence.
* **Expected Outcome:** The system loads into a minimal rescue shell environment (single-user mode).

---

## 🔍 Task 2: Understand and Configure systemd Targets

### ⚙️ Subtask 2.1: List Available Targets
* **Command:** 
  ```bash
  systemctl list-units --type=target --all
  ```
* **Expected Outcome:** Generates a detailed list of system targets including `multi-user.target`, `graphical.target`, and `rescue.target`.

### ⚙️ Subtask 2.2: Set Default Target
* **Set CLI Mode as Default:**
  ```bash
  sudo systemctl set-default multi-user.target
  ```
* **Verification:**
  ```bash
  systemctl get-default
  ```
* **Revert to Desktop Mode:**
  ```bash
  sudo systemctl set-default graphical.target
  ```

---

## 🔄 Task 3: Practice Switching Between Targets

### ⚙️ Subtask 3.1: Temporarily Switch to a Different Target
* **Switch to CLI Mode:**
  ```bash
  sudo systemctl isolate multi-user.target
  ```
* **Switch Back to GUI Mode:**
  ```bash
  sudo systemctl isolate graphical.target
  ```

### ⚙️ Subtask 3.2: Reboot into a Specific Target
* **Command:** 
  ```bash
  sudo systemctl reboot --boot-loader-entry=rescue.target
  ```
* **Expected Outcome:** The system directly reboots itself straight into rescue mode.

---

## 🏁 Conclusion
This lab session establishes foundational capabilities for handling `systemd` structures, allowing you to:
* Boot effectively into specific environment targets (`multi-user`, `graphical`, `rescue`).
* Change configuration behaviors globally using `systemctl` variables.
* Set permanent persistent target properties and approach core troubleshooting blocks.

### 💡 Troubleshooting Tips
* If a target fails to switch or load correctly, inspect error entries using:
  ```bash
  journalctl -xe
  ```
* For system hang scenarios, force a manual hard reboot and re-verify your system parameters or GRUB setup blocks.
* If `systemctl isolate` operations fail outright, map the requirement layout with:
  ```bash
  systemctl list-dependencies <target>
  ```
