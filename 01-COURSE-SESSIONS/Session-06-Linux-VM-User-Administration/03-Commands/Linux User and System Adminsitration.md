# 🐧 Linux Day 3: VM Health, Search, Archiving, & User Administration

<p align="left">
  <img src="https://img.shields.io/badge/Status-Completed-success?style=for-the-badge" alt="Status">
  <img src="https://img.shields.io/badge/Module-Session_06-blue?style=for-the-badge" alt="Module">
  <img src="https://img.shields.io/badge/Environment-GCP_Compute_Engine-orange?style=for-the-badge" alt="GCP">
  <img src="https://img.shields.io/badge/Author-Mahesh_Gummul-informational?style=for-the-badge" alt="Author">
</p>

---

## 🎯 Overview
This document catalogs the terminal commands executed during **Linux Day 3**. It bridges core system diagnostics, file archiving mechanisms, and enterprise user/group administration—core competencies for an infrastructure and DevOps engineer transitioning from Windows/VMware to Linux.

---

## 🖥️ 1. System Health & Performance Diagnostics

| Command | Category | Description | Production Use Case |
| :--- | :--- | :--- | :--- |
| `ssh-keygen` | Security | Generates public/private key pairs | Secure server access |
| `uname -a` | System | Prints kernel & system architecture | Verifying OS builds |
| `top` / `htop` | Monitoring | Real-time process & resource viewer | Spotting CPU/RAM bottlenecks |
| `uptime` | Monitoring | System run time & load averages | Checking server stability |
| `last` | Auditing | History of logins & system reboots | Security access tracking |
| `df -h` | Storage | Human-readable disk space usage | Preventing storage outages |
| `pwd` | Navigation| Prints absolute working directory | Verifying current location |
| `du` | Storage | Estimates file & folder space usage | Tracking large subfolders |
| `ping` | Networking| Tests network connectivity & ICMP | Checking IP reachability |
| `who` / `w` / `whoami` | Auditing | Identifies active users on the node | Multi-user session tracking |

> [!TIP]
> **Infrastructure Bridge:** `df -h` is your Linux equivalent to checking drive volumes and free space percentages in Windows Disk Management or vCenter datastore views.

---

## 🔍 2. File Searching & Log Inspection

```bash
cd /var/log
apt-get update && apt install plocate
locate *.log
find *.log