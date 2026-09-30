# 🏛️ LMS Enterprise Course Module: Linux System Administration, Nginx Web Server & Scripting

<p align="center">
  <img src="https://img.shields.io/badge/LMS_Level-Professional-blue?style=for-the-badge&logo=gradlescaled" alt="Level">
  <img src="https://img.shields.io/badge/Module-Session_07_Day_4-orange?style=for-the-badge&logo=linux" alt="Module">
  <img src="https://img.shields.io/badge/Total_Commands-46_Tracked_Steps-success?style=for-the-badge&logo=terminal" alt="Steps">
  <img src="https://img.shields.io/badge/Status-Verified_Production_Lab-informational?style=for-the-badge&logo=github" alt="Status">
</p>

---

## 📌 Module Overview & Objectives
Welcome to **Session 07 (Day 4)** of the enterprise infrastructure curriculum. This lab covers system version auditing, advanced user account aging policies via `chage`, Nginx web server deployment and service lifecycle control, and basic Bash shell script creation, permission hardening (`chmod +x`), and execution. Below is the complete, audit-ready operational record of all **46 terminal commands** executed during the live lab environment on GCP Compute Engine.

---

## 📑 Comprehensive 46-Step Command Registry

| Step | Command Execution | Operational Function & Engineering Context |
| :---: | :--- | :--- |
| **01** | `cd /` | Changes working directory to the root of the Linux filesystem. |
| **02** | `ls` | Lists directory contents and file attributes at root. |
| **03** | `cat /etc/os-release` | Displays operating system release details, version numbers, and distribution metadata. |
| **04** | `cd /tmp/` | Changes working directory to the temporary storage directory. |
| **05** | `ls` | Lists contents of the temporary directory. |
| **06** | `cd day-4` | Attempts to navigate into a directory named `day-4`. |
| **07** | `mkdir day-4` | Creates the `day-4` working directory since it did not exist. |
| **08** | `cd day-4/` | Navigates inside the newly created `day-4` directory. |
| **09** | `ls` | Lists directory contents inside `day-4`. |
| **10** | `vi jogi` | Opens the text editor to create or modify a file named `jogi`. |
| **11** | `ls` | Verifies file presence. |
| **12** | `vi jogi` | Re-opens file `jogi` to modify or update its text content. |
| **13** | `chage` | Examines the command syntax or updates user password expiration information. |
| **14** | `chage -i` | Tests flag parameters for password aging utilities. |
| **15** | `history` | Dumps the chronological terminal command execution buffer. |
| **16** | `chage -l om` | Lists password aging and expiration policy details for user account `om`. |
| **17** | `adduser om` | Interactively creates user account `om` and scaffolds its home environment. |
| **18** | `chage -l om` | Inspects account aging properties for user `om` post-creation. |
| **19** | `chage om` | Interactively modifies password expiration and aging parameters for user `om`. |
| **20** | `apt-get update` | Refreshes local Advanced Packaging Tool (APT) repository metadata lists. |
| **21** | `apt install nginx` | Installs the high-performance Nginx web server package. |
| **22** | `cd /var/www/html/` | Navigates into the default Nginx web server root publication directory. |
| **23** | `ls` | Lists files and default web assets located in the Nginx root directory. |
| **24** | `vi index.nginx-debian.html` | Edits the default Nginx HTML landing page file. |
| **25** | `history` | Dumps command history. |
| **26** | `vi index.nginx-debian.html` | Modifies the HTML page content further to customize web output. |
| **27** | `systemctl status nginx` | Checks the runtime operational status of the Nginx web service. |
| **28** | `systemctl stop nginx` | Stops the running Nginx web service. |
| **29** | `systemctl start nginx` | Starts the Nginx web service daemon. |
| **30** | `systemctl status nginx` | Verifies that Nginx has successfully restarted and is active. |
| **31** | `ls` | Lists current directory contents. |
| **32** | `cd /tmp/` | Changes directory back to `/tmp/`. |
| **33** | `ls` | Lists files in `/tmp/`. |
| **34** | `cd day-4/` | Navigates into the `day-4` lab directory under `/tmp/`. |
| **35** | `ls` | Lists contents of `day-4`. |
| **36** | `vi ankur.sh` | Creates and edits a custom shell script file named `ankur.sh`. |
| **37** | `cat ankur.sh` | Displays the script contents written inside `ankur.sh`. |
| **38** | `./ankur.sh` | Attempts to execute the script (initially fails due to missing executable permissions). |
| **39** | `ls -l` | Lists files in long format to inspect permissions and file metadata. |
| **40** | `chmod +x ankur.sh` | Adds executable permissions (`+x`) to the script file. |
| **41** | `ls` | Lists files in directory. |
| **42** | `ls -l` | Verifies that file permissions have successfully changed to executable (`-rwxr-xr-x`). |
| **43** | `./ankur.sh` | Successfully executes the script in the local environment context. |
| **44** | `ls` | Lists directory contents. |
| **45** | `ls -l` | Checks file listing details and attribute mappings. |
| **46** | `history` | Dumps the complete sequential execution log for the session. |

---

## 🛡️ Enterprise Security & Architecture Briefing

> [!NOTE]
> **Account Aging Governance (`chage`):** Enterprise compliance requires regular credential rotations. The `chage` utility controls password maximum age, warning periods, and account inactivity lockouts, replacing graphical Group Policy password rules found in Windows Active Directory.

> [!IMPORTANT]
> **Web Server Root & Service Lifecycle (`nginx`):** Nginx serves static assets directly from `/var/www/html/`. Managing service states via `systemctl` (`start`, `stop`, `status`) is a fundamental SRE skill for controlling Linux application daemons.

> [!TIP]
> **Executable Permissions (`chmod +x`):** Newly created text scripts cannot run directly as programs until execution flags are granted using `chmod +x`, transitioning the file from plain text into an operational command script.
