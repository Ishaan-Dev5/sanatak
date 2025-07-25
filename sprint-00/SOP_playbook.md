# SOP: Ansible Playbook

---

### Author Information

| Author      | Created on  | Version    |   Last updated on | Internal Reviewer | L0 Reviewer  | L1 Reviewer | L2 Reviewer      |
|-------------|-------------|------------|-----------------|----------------|-------------------|---------------|----------------------------------|
| Ishaan    | 22-07-25    | v1.0  |       22-07-25       | Rohit Chopra    |  Akshit/Nitik    | Taran        | Abhishek Dubey/ Rishab sharma |

---


## Table of Contents

1. [Introduction](#introduction)
2. [Introduction to playbook](#introduction-to-playbook)
3. [Prerequisites](#prerequisites)
4. [Required Inputs](#required-inputs) 
5. [Execution Steps](#execution-steps)
6. [Validation Checks](#Validation-checks)    
7. [Troubleshooting](#troubleshooting)
8. [Conclusion](#conclusion)
9. [FAQs](#FAQs) 
10. [Contact Information](#contact-information)  
11. [References](#references)

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

<img width="1480" height="352" alt="image" src="https://github.com/user-attachments/assets/5b6f8543-a882-42df-b854-e098a72127d9" />


### 2. Execute Playbook

```bash
   ansible-playbook -i inventory playbook.yml
```

<img width="1919" height="368" alt="image" src="https://github.com/user-attachments/assets/c5aa8934-4711-4f61-a081-3d19cbea0efc" />


### 3. Pass Extra Variables (if needed)

```bash
   ansible-playbook -i inventory playbook.yml -e "env=dev version=1.0"
```

<img width="1908" height="449" alt="image" src="https://github.com/user-attachments/assets/8dbcf6ad-8716-433e-b457-5ba97cdf8233" />


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

<img width="1520" height="351" alt="image" src="https://github.com/user-attachments/assets/195a1ef8-a80e-40f7-88fa-5a63c743c58b" />


### 2. Dry Run / Check Mode

**Purpose**: Simulates playbook execution without applying changes to the target systems.

```bash
   ansible-playbook site.yml --check -i inventory/prod.ini
```
<img width="1919" height="333" alt="image" src="https://github.com/user-attachments/assets/330a4a0b-dbcc-4632-aeb7-ac3225144424" />

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

## Conclusion

This SOP ensures reliable and secure execution of Ansible playbooks. Following the steps, validations, and best practices helps prevent errors and supports consistent automation. Always validate playbooks before use and check logs for troubleshooting


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















