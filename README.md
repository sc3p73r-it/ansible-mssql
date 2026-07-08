# Ansible Playbook: MS SQL Server 2025 on Ubuntu

This repository contains production-ready Ansible playbooks to automate the installation, configuration, initialization, and uninstallation of **Microsoft SQL Server 2025** and its command-line tools on Ubuntu systems. 

It features an automated fallback mechanism to safely deploy on newer distributions (like Ubuntu 26.04 LTS) using the verified `noble` (24.04) package tracks without dependency or licensing breaks.

---

## Features
* **Self-Healing Initialization**: Evaluates instance state dynamically to cleanly run unattended EULA licensing configurations.
* **System Environment Integration**: Automatically appends native SQL binaries (`sqlcmd`, `bcp`) to the structural system `$PATH`.

---

## Prerequisites

* **Ansible Control Node**: Ansible 2.15+ installed.
* **Target Managed Node(s)**: 
  * Ubuntu 24.04 (Noble) or Ubuntu 26.04 (Resolute).
  * Minimum **2 GB RAM** required by the database engine (Tested optimally on AWS `c7i-flex.large`).
  * SSH access with `sudo` privileges.

---

## Repository Structure

```text
├── inventory           # Host file declaring target database nodes
├── vars.yml            # Encrypted or plain configuration variables
├── install_mssql.yml   # Main installation playbook
└── uninstall_mssql.yml # Complete system teardown playbook
