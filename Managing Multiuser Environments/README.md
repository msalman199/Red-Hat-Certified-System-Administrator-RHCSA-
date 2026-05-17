# Managing Multiuser Environments

This repository contains a practical, hands-on guide to administering multiuser Linux environments, managing privileges with `su`/`sudo`, adjusting resource access permissions, controlling system targets, and managing containerized user isolation.

## 🎯 Objectives
By the end of this lab, you will be able to:
* **Administer Identities:** Create and maintain discrete user access profiles on Linux hosts.
* **Elevate Privileges Securely:** Fluidly cycle between system accounts using `su` and execute administrative actions with `sudo`.
* **Enforce Resource Isolation:** Configure Standard POSIX file permissions to protect cross-user assets.
* **Control System Operational Modes:** Switch runlevels seamlessly between command-line environments and visual desktops.
* **Apply Containerized Security:** Enforce non-root user ID execution runtime bounds within container boundaries.

## 📋 Prerequisites
* **OS:** A Linux-based environment (RHEL, CentOS, or Fedora recommended).
* **Access:** Administrative privileges or direct root shell access.
* **Tooling:** Basic command-line tool familiarity and `Podman` installed for container orchestration exercises.

### ⚙️ Setup Requirements
Initialize your workspace environment before starting the lab by provisioning two distinct trial system accounts:
```bash
sudo useradd user1
sudo useradd user2
sudo passwd user1
sudo passwd user2
```

---

## 🛠️ Step-by-Step Implementation

### Task 1: Log In as Different Users Using su and sudo

#### Subtask 1.1: Switch Users with `su`
Simulate an interactive user migration into another distinct profile space:
```bash
# Drop cleanly into the target user profile shell environment
su - user1

# Audit your active shell context identity
whoami
```
* **Expected Output:** `user1`

Return back to your primary login shell baseline space:
```bash
exit
```

#### Subtask 1.2: Execute Commands with `sudo`
Validate operational protection logic by attempting to read sensitive authentication maps as a standard low-privilege system user:
```bash
cat /etc/shadow
```
* **Expected Outcome:** `Permission denied`

Circumvent local constraint structures safely by applying root credential token passing filters:
```bash
sudo cat /etc/shadow
```
* **Expected Outcome:** Secured shadow directory mappings read cleanly onto the console stream.

Audit your current assigned permissions rules grid profile matrices:
```bash
sudo -l
```
* **Troubleshooting Tip:** If your profile encounters a `"user is not in the sudoers file"` alert block, re-inject the account into administrative wheel loops:
  ```bash
  sudo usermod -aG sudo yourusername
  ```

---

### Task 2: Switch Between Users and Understand Permissions

#### Subtask 2.1: Create and Test File Access
##### 👤 As user1
Initialize a private tracking note block within the local profile registry path:
```bash
su - user1
touch ~/user1_file.txt
echo "This is user1's file" > ~/user1_file.txt
```

##### 👤 As user2
Attempt to breach and parse across alternative private home boundaries:
```bash
su - user2
cat /home/user1/user1_file.txt
```
* **Expected Outcome:** `Permission denied`

Audit file permissions definitions to verify access controls:
```bash
ls -l /home/user1/user1_file.txt
```

#### Subtask 2.2: Modify File Permissions
##### 👤 As user1
Grant global, unprivileged read visibility permissions to the file:
```bash
su - user1
chmod 644 ~/user1_file.txt
```

##### 👤 As user2
Re-attempt extraction processing from the other user profile workspace:
```bash
su - user2
cat /home/user1/user1_file.txt
```
* **Expected Outcome:** Text content reads cleanly across profile isolation zones.
> 💡 **Key Concept:** Linux file mechanics use values (`Read=4`, `Write=2`, `Execute=1`) applied across owner, group, and global target rings to govern file system security bounds.

---

### Task 3: Configure Multiuser Targets

#### Subtask 3.1: Check Current Target
Query the running initialization environment manager to uncover the default active system profile run target:
```bash
systemctl get-default
```
* **Common System Layout Outputs:**
  * `graphical.target`: Boot tracks load completely into an interactive GUI layout mode.
  * `multi-user.target`: System loads strictly inside a headless text command prompt interface.

#### Subtask 3.2: Change Between Targets
Safely pivot the physical system states on the fly without interrupting core backend operations:
```bash
# Drop down live into a bare minimal text display terminal state
sudo systemctl isolate multi-user.target

# Re-spin background user graphics frameworks instantly
sudo systemctl isolate graphical.target

# Persistently set the system boot layer engine state for future starts
sudo systemctl set-default multi-user.target
```
* **Troubleshooting Tip:** If your GUI display locks up during local testing transitions, trigger the main window display manager manually:
  ```bash
  sudo systemctl start gdm  # Use lightdm if running Ubuntu/Debian flavors
  ```

---

### Task 4: Advanced Container User Management with Podman

Orchestrate a isolated runtime container instance bound to a specific arbitrary uid number layout allocation model:
```bash
podman run --user 1000 -it fedora /bin/bash
```
Check your active credentials environment inside the container space:
```bash
whoami
```
* **Expected Output:** Displays uid indicator `1000`, validating successful non-root platform isolation.

Drop the container thread engine when testing concludes:
```bash
exit
```

---

## 🔬 Additional Practice Exercises
* **Shared Storage Groups:** Provision a mutual system directory with sticky permissions rules enabling write functionality for all group participants.
* **Granular Sudo Trimming:** Adjust configuration strings inside `/etc/sudoers` restricting `user2` strictly to specific command lines.
* **SELinux Security Audits:** Evaluate context label attributes shifting across files created under differing user rings.

## 🧹 Lab Cleanup
Always clear out lab tracking users and return targets to normal settings after completing evaluation tasks:
```bash
# Purge lab identities completely alongside their directories
sudo userdel -r user1
sudo userdel -r user2

# Restore the graphical system loading baseline configurations
sudo systemctl set-default graphical.target
```

---

## 🏁 Conclusion
By completing this practical lab layout, you have mastered:
* Handling multi-user access mechanics across system boundaries.
* Managing privileges via system rules parameters.
* Shifting runtime configurations dynamically to optimize computing loads.

These core isolation practices form the foundation of secure container design standards within modern infrastructure ecosystems like **Red Hat OpenShift**.
