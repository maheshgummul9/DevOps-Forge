\# 🐧 Linux Day 3: Complete Step-by-Step Command \& System Administration Lab Reference



<p align="center">

&#x20; <img src="https://img.shields.io/badge/Status-Production\_Ready-success?style=for-the-badge\&logo=linux" alt="Status">

&#x20; <img src="https://img.shields.io/badge/Module-Session\_06-blue?style=for-the-badge\&logo=googlecloud" alt="Module">

&#x20; <img src="https://img.shields.io/badge/Total\_Commands-52\_Steps-orange?style=for-the-badge\&logo=terminal" alt="Commands">

&#x20; <img src="https://img.shields.io/badge/Author-Mahesh\_Gummul-informational?style=for-the-badge\&logo=github" alt="Author">

</p>



\---



\## 🏗️ Architectural Overview: Linux Identity \& Security Model



The following Mermaid diagram illustrates how Linux manages user identities, system groups, and superuser privileges locally, contrasting with Active Directory workflows:



```mermaid

graph TD

&#x20;   Root\[Root User / Superuser] -->|Manages Security| Sudoers\[/etc/sudoers via visudo/]

&#x20;   Root -->|Access Control| Shadow\[(/etc/shadow - Encrypted Hashes)]

&#x20;   Root -->|User Accounts| Passwd\[/etc/passwd - UIDs \& Shells]

&#x20;   Passwd -->|Contains| Users\[Local Users: kishore, om]

&#x20;   Group\[/etc/group] -->|Contains Groups| DevOpsGrp\[devops45 Group]

&#x20;   Users -->|usermod -a -G| DevOpsGrp

&#x20;   

&#x20;   style Root fill:#0B192C,stroke:#FF6700,stroke-width:2px,color:#fff

&#x20;   style Users fill:#1E3E62,stroke:#FF6700,stroke-width:2px,color:#fff

&#x20;   style DevOpsGrp fill:#FF6700,stroke:#0B192C,stroke-width:2px,color:#fff

&#x20;   style Shadow fill:#990000,stroke:#fff,stroke-width:2px,color:#fff

