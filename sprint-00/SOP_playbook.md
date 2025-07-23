# SOP: Ansible Playbook

---

### Author Information

| Author      | Created on  | Version    |   Last updated on | Internal Reviewer | L0 Reviewer  | L1 Reviewer | L2 Reviewer      |
|-------------|-------------|------------|-----------------|----------------|-------------------|---------------|----------------------------------|
| Ishaan    | 22-07-25    | v1.0  |       22-07-25       | Rohit Chopra    |  Akshit/Nitik    | Taran        | Abhishek Dubey/ Rishab sharma |

---


## Table of Contents

1. [Introduction](#introduction)
2. [What is Ansible Playbook?](#what-is-ansible-playbook)
3. [Why Ansible Playbook](#why-ansible-playbook)
4. [Prerequisites](#prerequisites)
5. [Required Inputs](#required-inputs) 
6. [Installation Steps](#installation-steps)  
   - [For Windows](#for-windows)  
   - [For Ubuntu / Debian-based Linux](#for-ubuntu--debian-based-linux)  
   - [For macOS using Homebrew](#for-macos-using-homebrew)  
7. [Troubleshooting](#troubleshooting)
8. [FAQs](#FAQs) 
9. [Contact Information](#contact-information)  
10. [References](#references)

---

## Introduction

This SOP outlines the standard procedure to execute the Ansible playbook reliably. It ensures consistent automation by detailing the objective, required inputs, validation checks, and step-by-step execution process.

---

## Introduction to Playbook
**To get an overview of playbook**: [Playbook Introduction]()



---

## Prerequisites

- A system with internet access
- Basic terminal/command line access
- Administrative/root privileges
- OS: Windows / Linux / macOS

---

## Required Inputs

| Parameter        | Description                                      |  Requirement                            |
|------------------|--------------------------------------------------|-----------------------------------------|
| `playbook`       | Path to the Ansible playbook file to execute     | Required                                |
| `inventory`      | Inventory file or host group to target           | Required                                |
| `vault_password` | Vault password file (if using encrypted secrets) | Required (if using Vault)               |
| `extra_vars`     | Dynamic variables passed at runtime              | Required (if playbook expects variables)|


```
---
## Troubleshooting

| **Issue**                           | **Resolution**                                                  |
|------------------------------------|------------------------------------------------------------------|
| `command not found: npm`           | Check if Node.js is properly installed and added to system PATH |
| npm version is outdated            | Run `npm install -g npm` to update                              |
| Permission denied errors on Linux  | Use `sudo`, or fix ownership with `chown`                       |


---
## FAQs

### 1.  Is npm installed automatically with Node.js?
Yes. When you install Node.js, npm is automatically installed as part of the package.



### 2. How do I check if npm is installed correctly?
Run the following command in your terminal or command prompt:
```
npm -v
```

### 3. How do I update npm to the latest version?
Use the command:
```
npm install -g npm@latest
```



---
## Contact Information

| Name         | Email address          |
|--------------|------------------------|
| Ishaan         | ishaan.aggarwal.snaatak@mygurukulam.co    |


---

## References

| **Title**                                 | **Link**                                                                                      |
|-------------------------------------------|-----------------------------------------------------------------------------------------------|
| Ansible Playbooks – Official Documentation| [Visit](https://docs.ansible.com/ansible/latest/user_guide/playbooks.html)                    |
| Ansible Inventory – Official Guide        | [Visit](https://docs.ansible.com/ansible/latest/user_guide/intro_inventory.html)              |
| Passing Variables to Playbooks            | [Visit](https://docs.ansible.com/ansible/latest/user_guide/playbooks_variables.html)          |
| Best Practices for Ansible Playbooks      | [Visit](https://docs.ansible.com/ansible/latest/tips_tricks/index.html)                       |

---















