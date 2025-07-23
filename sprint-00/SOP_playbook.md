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
6. [Execution Steps](#execution-steps)    
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

| **Requirement**         | **Why It's Needed**                                                                 |
|-------------------------|--------------------------------------------------------------------------------------|
| **Ansible**             | Main automation tool that runs your playbooks.                                      |
| **SSH Access**          | For connecting to and managing remote hosts (Linux nodes).                          |
| **Python 3**            | Required on both control node and target machines (Ansible depends on it).          |
| **Basic YAML Knowledge**| Playbooks are written in YAML format, so understanding indentation & syntax is needed. |

---

## Required Inputs

| Parameter        | Description                                      |  Requirement                            |
|------------------|--------------------------------------------------|-----------------------------------------|
| `playbook`       | Path to the Ansible playbook file to execute     | Required                                |
| `inventory`      | Inventory file or host group to target           | Required                                |
| `vault_password` | Vault password file (if using encrypted secrets) | Required (if using Vault)               |
| `extra_vars`     | Dynamic variables passed at runtime              | Required (if playbook expects variables)|

---

## Execution Steps

### 1. Run Connectivity Check
```bash
   ansible -i inventory all -m ping
```

### 2. Execute Playbook

```bash
   ansible-playbook -i inventory playbook.yml
```

### 3. Pass Extra Variables (if needed)

```bash
   ansible-playbook -i inventory playbook.yml -e "env=dev version=1.0"
```

### 4. - Use Vault (if secrets are encrypted)

```bash
   ansible-playbook -i inventory playbook.yml --ask-vault-pass
```
---
## Validation Checks

### 1. Syntax Check

**Purpose**: Verifies that the playbook's YAML structure and Ansible syntax are valid.

```bash
   ansible-playbook site.yml --syntax-check
```

### 2.  Dry Run / Check Mode

**Purpose**: Simulates playbook execution without applying changes to the target systems.


```bash
   ansible-playbook site.yml --check -i inventory/prod.ini
```


---

## Troubleshooting

### Common errors
    - SSH permission denied → Check user/SSH key.
    - Missing vars → Ensure all required variables are provided.
    - Vault decryption failed → Verify vault password file.

### Check logs : Use -vvv for verbose output

```bash
ansible-playbook site.yml -i inventory/prod.ini -vvv
```

---

## FAQs



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















