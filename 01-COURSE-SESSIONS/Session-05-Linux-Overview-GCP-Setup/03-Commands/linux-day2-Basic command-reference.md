# Linux Day 2: Comprehensive Command Reference & Lab Documentation

**Author:** Mahesh Ravindra Gummul  
**Date:** September 30, 2026  
**Environment:** GCP Compute Engine (Linux)  

---

## Overview
This document serves as the official structured technical reference for **Linux Day 2**, documenting the practical terminal operations performed during environment configuration, file manipulation, and system resource inspection.

---

## 1. SSH Key Management & Navigation Commands

* **`ssh-keygen`**
  * *What it does:* Generates a cryptographic public/private key pair.
  * *Why it is used:* Replaces insecure password-based authentication with secure, key-based cryptographic login.
  * *Production Context:* Essential for automated cloud infrastructure provisioning and CI/CD agent access.

* **`cd /root/.ssh/`**
  * *What it does:* Changes the current working directory to the root user's SSH configuration folder.
  * *Why it is used:* Location where authorized keys, known hosts, and cryptographic identity files are managed.

* **`ls` / `ls -la`**
  * *What it does:* Lists directory contents. `-l` provides a detailed view (permissions, owners, sizes), while `-a` reveals hidden configuration files.
  * *Why it is used:* To verify files, check permissions, and audit directory structures.

* **`cat id_ed25519.pub`**
  * *What it does:* Outputs the contents of the Ed25519 public key file to the terminal.
  * *Why it is used:* To copy public keys for deployment onto remote target servers or version control systems like GitHub.

* **`pwd`**
  * *What it does:* Prints the Present Working Directory path.
  * *Why it is used:* Verifies current absolute filesystem location before executing operations.

---

## 2. Directory & File Operations

* **`cd /tmp/`**
  * *What it does:* Navigates to the temporary system scratchpad directory.
  * *Why it is used:* Ideal for testing scripts and running labs since contents are automatically cleared upon system reboots.

* **`mkdir sushant`**
  * *What it does:* Creates a new directory named `sushant`.
  * *Why it is used:* To maintain clean, structured directory hierarchies.

* **`touch mohitfile`**
  * *What it does:* Creates an empty file or updates the timestamp of an existing one.
  * *Why it is used:* Rapidly initializes scratch files for testing configurations.

* **`rm mohitfile`**
  * *What it does:* Permanently deletes a file.
  * *WARNING:* Linux bypasses a Recycle Bin; `rm` execution is immediate and unrecoverable without backups.

---

## 3. File Viewing & Inspection Utilities

* **`cat indra`**
  * *What it does:* Dumps the full contents of a file to standard output.
  * *Why it is used:* Best for reading short configuration files quickly.

* **`more indra`**
  * *What it does:* Paginates file content screen-by-screen.
  * *Why it is used:* Prevents terminal buffer overflow when examining extensive text files.

* **`head -10 indra`** & **`tail -10 indra`**
  * *What it does:* Displays the first (`head`) or last (`tail`) 10 lines of a file.
  * *Why it is used:* Essential during troubleshooting to quickly check log file headers or review real-time activity at the end of active logs.

* **`vi indra`**
  * *What it does:* Opens the universal modal text editor.
  * *Why it is used:* Essential for editing configuration files (`sshd_config`, Nginx blocks) directly on headless production servers.

---

## 4. File Management & Renaming

* **`cp indra gopal`**
  * *What it does:* Copies source file `indra` to destination `gopal`.
  * *Why it is used:* Creates safe backups prior to modifying production code or config files.

* **`mv indra shashi`**
  * *What it does:* Moves or renames files across the filesystem.
  * *Why it is used:* Restructures files and updates naming conventions.

---

## 5. System & Network Discovery Commands

* **`hostname` / `hostname -i` / `hostname -e`**
  * *What it does:* Inspects node identification names and associated network IP addresses.
  * *Why it is used:* Validates node identity inside container clusters and virtualized cloud networks.

* **`curl ifconfig.me`**
  * *What it does:* Queries an external web service to retrieve the server's public IP address.
  * *Why it is used:* Quick verification of outbound NAT and public network routing configurations.

* **`uname -a`**
  * *What it does:* Prints comprehensive kernel release, version, and architecture information.
  * *Why it is used:* Ensures software compatibility before package installations.

* **`whoami`**
  * *What it does:* Displays the active user account context.
  * *Why it is used:* Security validation to confirm execution privileges (e.g., root vs. standard user).

---

## 6. Process Monitoring & System Resources

* **`ps -aef`**
  * *What it does:* Snapshots all active system processes across every user context.
  * *Why it is used:* Traces parent-child process trees and identifies stuck applications.

* **`ps -aef | grep [service]`**
  * *What it does:* Filters process tables for targeted software threads (e.g., systemd, Java).
  * *Why it is used:* Rapid status verification for background services.

* **`top`**
  * *What it does:* Launches a dynamic, real-time performance dashboard for CPU and RAM consumption.
  * *Why it is used:* Primary tool for diagnosing resource bottlenecks during performance incidents.

* **`free -h`**
  * *What it does:* Reports available and consumed physical/swap memory in human-readable formats (GB/MB).
  * *Why it is used:* Quick diagnosis for out-of-memory (OOM) conditions on enterprise nodes.

* **`history`**
  * *What it does:* Outputs historical chronological lists of executed terminal commands.
  * *Why it is used:* Auditing workflows and generating structured documentation.

---

### Pro-Tip for Git Push
To save this into your local repository structure, run:
```bash
cd C:\Mahesh-DevOps\
git add 03-Commands/linux-day2-command-reference.md
git commit -m "docs: add Linux Day 2 comprehensive command reference"
git push origin main