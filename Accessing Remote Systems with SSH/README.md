# Accessing Remote Systems with SSH

This repository contains a step-by-step practical guide to mastering Secure Shell (SSH) workflows, implementing secure passwordless key-based authentication, and executing secure file transfers.

## 🎯 Objectives
By the end of this lab, you will be able to:
* **Establish Remote Sessions:** Understand and configure fundamental SSH architecture components.
* **Harden Authentication:** Implement secure, modern public-private cryptographic key pairs.
* **Transfer Assets Securely:** Utilize Secure Copy Protocol (`scp`) to move data packets reliably across network boundaries.
* **Manage Network Nodes:** Maintain remote servers with a focus on cloud-native and container infrastructure design paradigms.

## 📋 Prerequisites
* **Local Machine:** A Linux-based operational environment (Ubuntu, CentOS, Fedora, or RHEL recommended).
* **Remote Machine:** A distinct Linux server instance reachable across your local or cloud network matrix.
* **Skills:** Ground-level comfort executing core standard commands inside a Linux terminal shell.

### 📦 Required Package Layers
Ensure the deployment environments have the necessary packages loaded:
* **Local Machine:** Requires OpenSSH Client libraries (`openssh-client` or `openssh-clients`).
* **Remote Server:** Requires OpenSSH Daemon engines (`openssh-server`).

---

## 🛠️ Step-by-Step Implementation

### Task 1: Set Up and Connect to a Remote System Using SSH

#### Subtask 1.1: Verify SSH Installation
##### 💻 Local Client Verification
Query the local terminal to verify the client binary version:
```bash
ssh -V
```
* **Troubleshooting:** If missing, update your repository indices and provision the component:
  ```bash
  # For Ubuntu / Debian
  sudo apt update && sudo apt install openssh-client -y

  # For CentOS / RHEL / Fedora
  sudo dnf install openssh-clients -y
  ```

##### 🖥️ Remote Server Verification
Log onto your hosting engine console and check the background service daemon status:
```bash
sudo systemctl status sshd
```
* **Troubleshooting:** If the listener is down or disabled, wake the system daemon:
  ```bash
  sudo systemctl start sshd && sudo systemctl enable sshd
  ```

#### Subtask 1.2: Connect to the Remote Server
Initiate a traditional network-handshake mapping over to the target machine (replace placeholders with your real environment variables):
```bash
ssh username@remote_server_ip
```
* **Expected Outcome:** The terminal prompts for the remote password profile. Upon successful input, your terminal window context switches straight into the remote node shell prompt.

---

### Task 2: Implement SSH Key-Based Authentication

#### Subtask 2.1: Generate SSH Key Pair
##### 💻 Local Client Side
Generate a highly secure, modern elliptic curve cryptographic signature file:
```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```
* **Parameter Breakdown:**
  * `-t ed25519`: Specifies the modern, fast, and secure Ed25519 algorithm.
  * `-C`: Appends a descriptive tracking comment onto the end of the public block.
* **Execution:** Tap `Enter` to accept the default file path assignment (`~/.ssh/id_ed25519`).
* **Expected Outcome:** Generates your private key (`id_ed25519`) and public key (`id_ed25519.pub`) files.

#### Subtask 2.2: Copy the Public Key to the Remote Server
Export your local identity mapping block across the network structure over to the remote host:
```bash
ssh-copy-id -i ~/.ssh/id_ed25519.pub username@remote_server_ip
```
* **Expected Outcome:** The block automatically appends inside the remote file path (`~/.ssh/authorized_keys`).

##### 🔬 Passwordless Verification Test
Re-run the initiation routine from your local workstation node:
```bash
ssh username@remote_server_ip
```
* **Expected Result:** The system bypasses password checks and grants instant secure interactive shell access.

---

### Task 3: Securely Transfer Files Using scp

#### Subtask 3.1: Copy a File from Local to Remote
Push local dataset items up into a designated remote directory path safely over an encrypted tunnel:
```bash
scp localfile.txt username@remote_server_ip:/remote/directory/
```

#### Subtask 3.2: Copy a File from Remote to Local
Pull files from remote directories down into your local workstation framework paths:
```bash
scp username@remote_server_ip:/remote/directory/remotefile.txt ~/local/directory/
```

---

## 💡 Troubleshooting Tips

* **🔒 Permissions Hardening Issues:** SSH drops connections if access permissions are loose. Enforce proper access rules on both environments:
  ```bash
  chmod 700 ~/.ssh
  chmod 600 ~/.ssh/authorized_keys
  chmod 600 ~/.ssh/id_ed25519
  ```
* **🚫 Connection Refused:** Ensure that host firewalls permit active inbound traffic routing over Port 22 (`sudo firewall-cmd --add-service=ssh --permanent && sudo firewall-cmd --reload`).
* **🔑 Key Auth Bypassed:** If the system falls back to password prompts, check the remote daemon config rules file (`/etc/ssh/sshd_config`) to ensure `PubkeyAuthentication yes` is enabled.

---

## 🏁 Conclusion
By completing this practical lab, you have mastered:
* Provisioning and maintaining reliable remote administrative connection paths.
* Disabling passwords in favor of secure cryptographic key infrastructures.
* Managing secure file transfer operations across distributed hosts.

These core competencies form the bedrock of running systems efficiently inside modern cloud architectures, remote orchestration setups, and advanced container ecosystems like **Red Hat OpenShift**.
