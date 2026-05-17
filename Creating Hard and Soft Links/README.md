# Creating Hard and Soft Links

This repository contains a hands-on practical guide to mastering the storage referencing layer in Linux. You will learn how to implement hard links and symbolic (soft) links, audit inode tracking parameters, map data block allocations, and navigate filesystem boundaries.

## 🎯 Objectives
By the end of this lab, you will be able to:
* **Deconstruct Link Types:** Understand structural differences between hard data pointers and soft filename pointers.
* **Manage Inode Blocks:** Create and verify hard links using shared storage references.
* **Orchestrate Soft Pointers:** Deploy flexible symbolic links (`ln -s`) across directories.
* **Navigate Boundary Constraints:** Identify and troubleshoot cross-filesystem link restrictions.
* **Audit File States:** Use system metrics to inspect active link counts and detect broken pathways.

## 📋 Prerequisites
* **OS:** A Linux-based environment (Fedora, CentOS, Ubuntu, or RHEL recommended).
* **Access:** Terminal terminal connection with standard privileges (root/sudo access required for multi-mount validation).
* **Profile:** A standard non-root user account is highly recommended for safety.

---

## 🛠️ Step-by-Step Implementation

### Task 1: Create and Delete Hard Links

#### Subtask 1.1: Create a Sample File
Initialize a dedicated sandbox environment directory and generate a baseline tracking text file:
```bash
mkdir link_lab && cd link_lab
echo "This is the original file." > original.txt
```
Verify successful asset layout compilation:
```bash
cat original.txt
```
* **Expected Output:** `This is the original file.`

#### Subtask 1.2: Create a Hard Link
Generate a secondary directory entry pointer pointing back to the same physical data structure block:
```bash
ln original.txt hardlink.txt
```
Audit the filesystem structural indices to verify entry behaviors:
```bash
ls -li
```
> 💡 **Key Concept:** Both `original.txt` and `hardlink.txt` will reveal matching **inode numbers** (the leftmost integer columns). This proves they point directly to the exact same physical block of underlying hardware storage.

#### Subtask 1.3: Test Hard Link Behavior
Inject new content records directly through the newly created hard link file pathway:
```bash
echo "Appended via hard link." >> hardlink.txt
```
Query both file structures sequentially to witness live synchronization:
```bash
cat original.txt
cat hardlink.txt
```
* **Expected Outcome:** Both files reflect the exact same updated contents instantly, because they share one underlying data array pool.

#### Subtask 1.4: Delete the Hard Link
Purge the hard link reference file entry out of your localized directory layout tree:
```bash
rm hardlink.txt
```
Verify the storage integrity of the primary target asset link:
```bash
cat original.txt
```
* **Expected Outcome:** The baseline `original.txt` file content survives completely uncorrupted. The data block is preserved as long as the system tracking node link counter is greater than zero.

---

### Task 2: Create and Delete Symbolic (Soft) Links

#### Subtask 2.1: Create a Symbolic Link
Construct a soft path shortcut that points strictly to the string name of the target file rather than its inode:
```bash
ln -s original.txt symlink.txt
```
Verify the creation and check the system layout maps:
```bash
ls -l
```
* **Expected Outcome:** `symlink.txt` displays an arrow indicator (`->`) pointing straight towards its master file entry (`original.txt`).

#### Subtask 2.2: Test Symbolic Link Behavior
Extract content text directly through the soft shortcut line:
```bash
cat symlink.txt
```
* **Expected Outcome:** Displays the inner text lines of `original.txt`.

Now, drop the source target asset to observe the impact on your soft link:
```bash
rm original.txt
cat symlink.txt
```
* **Expected Outcome:** The system outputs an explicit `No such file or directory` failure block. Because the target text name is missing, the soft pointer breaks and points to a dead end.

#### Subtask 2.3: Recreate and Delete the Symbolic Link
Resurrect the exact file identity mapping by rebuilding the matching structural filename target:
```bash
echo "New content." > original.txt
```
Test the shortcut interface line to observe immediate self-healing:
```bash
cat symlink.txt
```
Clean up the workspace by dropping the soft link component directly:
```bash
rm symlink.txt
```

---

### Task 3: Manage Links Across Filesystems

#### Subtask 3.1: Attempt to Create a Hard Link Across Filesystems
Identify distinct system mount points on your machine (the `/tmp` path frequently operates on independent storage partitions):
```bash
df -h /tmp
```
Attempt to force a hard reference block boundary assignment over into that alternative storage array:
```bash
ln original.txt /tmp/hardlink_fail.txt
```
* **Expected Outcome:** `Error: Invalid cross-device link`. Hard links are strictly forbidden from spanning across separate isolated filesystem structures.

#### Subtask 3.2: Create a Symbolic Link Across Filesystems
Use the flexibility of symbolic links to clear drive space borders by passing an absolute tracking variable path:
```bash
ln -s \$(pwd)/original.txt /tmp/symlink_success.txt
```
Verify access tracking out from the shared system temp storage node:
```bash
cat /tmp/symlink_success.txt
```
* **Expected Outcome:** The file content is read and printed successfully across device frameworks.

---

## 💡 Troubleshooting Tips
* **Dangling (Red-Text) Links:** If a soft link fails, check the name structure accuracy of the underlying target file or path using `ls -l`.
* **Deep Inode Analysis:** Use the `stat` command to get an in-depth breakdown of link counts, inode configurations, and access properties:
  ```bash
  stat original.txt
  ```
* **Access Restraints:** If link setups trigger errors, ensure you have sufficient execution permissions (`rwx`) across both the source elements and the destination folders.

## 🏁 Conclusion
By executing this lab tracking structure, you have mastered:
* Operating hard links to maintain data persistence across path adjustments.
* Implementing symbolic links to cross logical boundaries and build storage maps.
* Troubleshooting system boundaries and monitoring inode states.

These data reference mechanics are critical for managing configurations, mounting runtime storage paths, and orchestrating deployment containers inside systems like **Red Hat OpenShift**.
