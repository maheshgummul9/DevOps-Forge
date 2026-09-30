# 🏛️ LMS Enterprise Course Module: Linux System & User Administration

<p align="center">
  <img src="https://img.shields.io/badge/LMS_Level-Professional-blue?style=for-the-badge&logo=gradlescaled" alt="Level">
  <img src="https://img.shields.io/badge/Module-Session_06-orange?style=for-the-badge&logo=linux" alt="Module">
  <img src="https://img.shields.io/badge/Total_Commands-52_Tracked_Steps-success?style=for-the-badge&logo=terminal" alt="Steps">
  <img src="https://img.shields.io/badge/Status-Verified_Production_Lab-informational?style=for-the-badge&logo=github" alt="Status">
</p>

---

## 📌 Module Overview & Objectives
Welcome to **Session 06** of the enterprise infrastructure curriculum. This module bridges traditional infrastructure foundations with Linux administration standards. Below is the complete, audit-ready operational record of all **52 terminal commands** executed during the live lab environment on GCP Compute Engine.

---

## 📑 Comprehensive 52-Step Command Registry

| Step | Command Execution | Operational Function & Engineering Context |
| :---: | :--- | :--- |
| **01** | `ssh-keygen` | Generates a cryptographic public/private key pair for secure, passwordless server access. |
| **02** | `uname -a` | Prints kernel release, version, and hardware architecture for software compatibility checks. |
| **03** | `top` | Launches a real-time, dynamic monitor of active system processes and CPU/RAM load. |
| **04** | `htop` | An enhanced, interactive process viewer featuring a color-coded interface for resource tracking. |
| **05** | `uptime` | Displays system run time, active user sessions, and 1, 5, and 15-minute load averages. |
| **06** | `last` | Audits historical user logins and system reboots by inspecting `/var/log/wtmp`. |
| **07** | `df` | Reports raw file system disk space allocation across mounted storage volumes. |
| **08** | `df -h` | Formats disk utilization metrics into **h**uman-readable values (MB, GB) to prevent storage limits. |
| **09** | `pwd` | Prints the absolute path of the **P**resent **W**orking **D**irectory. |
| **10** | `du` | Estimates file and directory space utilization across specific tree branches. |
| **11** | `ping www.google.com` | Tests outbound network routing, packet transmission, and DNS name resolution. |
| **12** | `who` | Lists all active user accounts currently logged into the virtual machine. |
| **13** | `w` | Displays logged-in users alongside the specific processes or commands they are executing. |
| **14** | `whoami` | Prints the username string of the currently active security context. |
| **15** | `ls` | Lists directory contents and file attributes. |
| **16** | `cd /var/log` | Changes directory into the central operating system and service log repository. |
| **17** | `ls` | Lists logs and tracking files inside the log directory. |
| **18** | `locate *.log` | Searches the file name database for log files (requires an active indexing database). |
| **19** | `apt-get update` | Refreshes local Advanced Packaging Tool software repository metadata lists. |
| **20** | `apt install plocate` | Installs `plocate`, a modern, lightning-fast file indexing and search utility. |
| **21** | `locate *.log` | Successfully queries the updated file index database for all `.log` assets. |
| **22** | `ls` | Checks directory contents. |
| **23** | `locate *.log` | Re-runs the index database search to confirm results. |
| **24** | `find *.log` | Recursively searches the live file system directly from the working directory. |
| **25** | `locate '*.log'` | Queries the database using single quotes to handle wildcard parameters safely. |
| **26** | `mkdir myfiles ; touch ...` | Creates a test directory and uses Bash brace expansion to initialize three blank files instantly. |
| **27** | `ls` | Confirms the new directory structure was created successfully. |
| **28** | `ls myfiles` | Lists individual file entries inside the created `myfiles` subfolder. |
| **29** | `tar -cvf allfiles.tar ...` | Bundles and creates (`-c`), verbosely displays (`-v`), and names (`-f`) an uncompressed archive. |
| **30** | `ls` | Verifies the newly generated archive bundle file exists in the directory. |
| **31** | `tar -xvf allfiles.tar` | Extracts (`-x`) the archive bundle back out into its original folder structure. |
| **32** | `adduser kishore` | Interactively creates user account `kishore` and scaffolds an isolated home directory. |
| **33** | `su kishore` | **S**witches **U**ser context to test permissions under account `kishore`. |
| **34** | `passwd kishore` | Modifies or sets the secure authentication password for user `kishore`. |
| **35** | `usrdel kishore` | *(Intentional Typo)* Generates an error, demonstrating standard syntax validation. |
| **36** | `userdel kishore` | Safely and properly removes the specified user account from the system registry. |
| **37** | `su kishore` | Attempts to switch user context (fails because the account was deleted in step 36). |
| **38** | `addgroup devops45` | Creates a new system-level security and access group named `devops45`. |
| **39** | `getent group` | Queries system database entries to verify group existence and details. |
| **40** | `adduser om` | Creates new user account `om`. |
| **41** | `getent group` | Verifies group database entries following account creation. |
| **42** | `usermod -a -G ...` | Modifies user account `om`, appending (`-a`) them to secondary security group (`-G`) `devops45`. |
| **43** | `getent group` | Confirms user `om` is successfully nested inside group `devops45`. |
| **44** | `chage` | Examines or updates user account password aging, maximum life, and warning policies. |
| **45** | `cd /etc/passwd` | *(Attempted path traversal on a file)* Demonstrates path handling error handling. |
| **46** | `cd /etc/` | Navigates into `/etc`, the central configuration directory for Linux systems. |
| **47** | `ls` | Lists configuration files and system templates. |
| **48** | `cat passwd` | Displays system user accounts, user IDs (UID), group IDs (GID), and default shells. |
| **49** | `cat shadow` | Displays secure encrypted password hashes and security aging constraints. |
| **50** | `cat group` | Displays system security groups and associated member lists. |
| **51** | `vi sudoers` | Opens the superuser security policy configuration template. |
| **52** | `history` | Dumps the sequential, chronological execution log of all session terminal entries. |

---

## 🛡️ Enterprise Security & Architecture Briefing

> [!NOTE]
> **Identity Architecture Context:** While Windows environments rely on centralized Active Directory (ADUC) structures, standalone Linux instances manage user profiles, UIDs, and access permissions via local flat database files stored in `/etc/`.

> [!WARNING]
> **Production Security Compliance (`/etc/shadow`):** 
> System configuration file `/etc/passwd` is world-readable by design, but `/etc/shadow` contains sensitive, encrypted password hashes and is strictly restricted to the `root` administrative context. Treat this file with the same security severity as an Active Directory `NTDS.dit` database export.

> [!IMPORTANT]
> **Administrative Best Practice:** Never edit `/etc/sudoers` directly using basic text editors like `vi`. Always invoke **`visudo`**, which automatically compiles and validates syntax rules before saving changes to prevent permanent administrative lockouts.

---

### 📂 Curriculum Repository Reference
`C:\Users\Lenovo\OneDrive\Desktop\Devops\Mahesh-DevOps-Corrected-Architecture\01-COURSE-SESSIONS\Session-06-Linux-VM-User-Administration\03-Commands\Linux User and System Adminsitration.md`