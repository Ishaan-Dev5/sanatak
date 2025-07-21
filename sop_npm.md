# SOP: NPM(Node Package Manager)

---

| Author      | Created on  | Version    | Last updated by | Last edited on |
|-------------|-------------|------------|-----------------|----------------|
| Ishaan    | 21-07-25    | version 1  | Ishaan        | 21-07-25       |

## Introduction
This SOP provides a standardized, step-by-step procedure to install Node Package Manager (NPM) on various operating systems..


## Table of Contents

1. [Why ansible playbook?](#why-ansible-playbook)
2. [What is ansible playbook?](#what-is-ansible-playbook)
3. [Prerequisites](#Prerequisites)  
4. [Required Inputs](#required-inputs)
3. [Commands and usage](#commands--usage)
     - [Run syntax check](#1-run-syntax-check-optional-but-recommended)
     - [Run dry-run](#2-run-dry-run-optional)
     - [Execute the playbook](#3-execute-the-playbook)
4. [Troubleshooting](#troubleshooting)
     - [Common errors](#common-errors)
     - [Check logs](#check-logs--use--vvv-for-verbose-output)
6. [Contacts](#contacts)
7. [References](#references)


## Introduction to NPM
**To explore benefits of playbook**: [Playbook Introduction](https://github.com/snaatak-Downtime-Crew/Documentation/blob/adil_scrums_48/common_stack/ansible/playbook/intro/README.md#2-why-ansible-playbook)

## What does NPM stand for and why is it important?
**To get an overview of playbook**: [Playbook Introduction](https://github.com/snaatak-Downtime-Crew/Documentation/blob/adil_scrums_48/common_stack/ansible/playbook/intro/README.md#3-what-is-ansible-playbook)

## Prerequisites

- A system with internet access
- Basic terminal/command line access
- Administrative/root privileges
- OS: Windows / Linux / macOS

## Installation Steps

### For Windows

### 1. Download Node.js Installer:
- Visit: https://nodejs.org
- Choose LTS version for stability.
- 
### 2. Run the Installer:
- Double-click the downloaded .msi file.
- Accept license agreement.
- Choose default options.
- Ensure the “npm package manager” option is selected during setup.
- 
### 3. Verify Installation:
- node -v
- npm -v

## Troubleshooting

### Common errors
    - SSH permission denied → Check user/SSH key.
    - Missing vars → Ensure all required variables are provided.
    - Vault decryption failed → Verify vault password file.

### Check logs : Use -vvv for verbose output

```bash
ansible-playbook site.yml -i inventory/prod.ini -vvv
```


## Contacts

| Name            | Email Address                                 |
|-----------------|-----------------------------------------------|
| Nishkarsh Kumar | nishkarsh.kumar.snaatak@mygurukulam.co        |


## References

| **Title**                                 | **Link**                                                                                      |
|-------------------------------------------|-----------------------------------------------------------------------------------------------|
| Ansible Playbooks – Official Documentation| [Visit](https://docs.ansible.com/ansible/latest/user_guide/playbooks.html)                    |
| Ansible Inventory – Official Guide        | [Visit](https://docs.ansible.com/ansible/latest/user_guide/intro_inventory.html)              |
| Passing Variables to Playbooks            | [Visit](https://docs.ansible.com/ansible/latest/user_guide/playbooks_variables.html)          |
| Best Practices for Ansible Playbooks      | [Visit](https://docs.ansible.com/ansible/latest/tips_tricks/index.html)                       |

---
Collapse













