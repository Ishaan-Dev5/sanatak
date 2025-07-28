<img width="250" height="200" alt="ansible-large" src="https://github.com/user-attachments/assets/63be2f72-9c36-4e7c-8513-0b1223c69d4c" />




# SOP: Ansible Playbook

---

### Author Information

| **Author**   | **Created on** | **Version** | **Last updated by** | **Last edited on** | **Level** | **Reviewer**  |
|--------------|----------------|-------------|---------------------|--------------------|-----------|---------------|
| Ishaan    | 22-07-25    | v1.0  |  Ishaan  |22-07-25   | Internal    | Rohit Chopra    | 

---


## Table of Contents

1. [Introduction](#1-introduction)
2. [What is playbook](#2-what-is-playbook)
3. [Prerequisites](#3-prerequisites)
4. [Required Inputs](#4-required-inputs) 
5. [Execution Steps](#5-execution-steps)
6. [Validation Checks](#6-Validation-checks)    
7. [Troubleshooting](#7-troubleshooting)
8. [Conclusion](#8-conclusion)
9. [FAQs](#9-FAQs) 
10. [Contact Information](#10-contact-information)  
11. [References](#11-references)

---

## 1. Introduction

This SOP outlines the standard procedure to execute the Ansible playbook reliably. It ensures consistent automation by detailing the objective, required inputs, validation checks, and step-by-step execution process.

---

## 2. What is Playbook
**To get an overview of playbook**: [Playbook Introduction](https://github.com/Snaatak-Apt-Get-Swag/documentation/blob/a551389066be42aa76214e273a2fdb4c4ba62375/Ansible/Playbook/Introduction/README.md)



---

## 3. Prerequisites

| **Requirement**         | **Why It's Needed**                                                                 |
|-------------------------|--------------------------------------------------------------------------------------|
| **Ansible**             | Main automation tool that runs your playbooks.                                      |
| **SSH Access**          | For connecting to and managing remote hosts (Linux nodes).                          |
| **Python 3**            | Required on both control node and target machines (Ansible depends on it).          |
| **Basic YAML Understanding**| Playbooks are written in YAML format, so understanding indentation & syntax is needed. |

---

## 4. Required Inputs

| Parameter        | Description                                      |  Requirement                            |
|------------------|--------------------------------------------------|-----------------------------------------|
| `playbook`       | Path to the Ansible playbook file to execute     | Required                                |
| `inventory`      | Inventory file or host group to target           | Required                                |
| `vault_password` | Vault password file (if using encrypted secrets) | Required (if using Vault)               |
| `extra_vars`     | Dynamic variables passed at runtime              | Required (if playbook expects variables)|

---

## 5. Execution Steps

- ### 5.1. Run Connectivity Check
```bash
   ansible -i inventory all -m ping
```

<img width="1480" height="352" alt="image" src="https://github.com/user-attachments/assets/5b6f8543-a882-42df-b854-e098a72127d9" />


- ### 5.2. Execute Playbook

```bash
   ansible-playbook -i inventory playbook.yml
```

<img width="1919" height="368" alt="image" src="https://github.com/user-attachments/assets/c5aa8934-4711-4f61-a081-3d19cbea0efc" />


- ### 5.3. Pass Extra Variables (if needed)

```bash
   ansible-playbook -i inventory playbook.yml -e "env=dev version=1.0"
```

<img width="1908" height="449" alt="image" src="https://github.com/user-attachments/assets/8dbcf6ad-8716-433e-b457-5ba97cdf8233" />


- ### 5.4. - Use Vault (if secrets are encrypted)

```bash
   ansible-playbook -i inventory playbook.yml --ask-vault-pass
```
---
## 6. Validation Checks

- ### 6.1. Syntax Check

**Purpose**: Verifies that the playbook's YAML structure and Ansible syntax are valid.

```bash
   ansible-playbook site.yml --syntax-check
```

<img width="1520" height="351" alt="image" src="https://github.com/user-attachments/assets/195a1ef8-a80e-40f7-88fa-5a63c743c58b" />


- ### 6.2. Dry Run / Check Mode

**Purpose**: Simulates playbook execution without applying changes to the target systems.

```bash
   ansible-playbook site.yml --check -i inventory/prod.ini
```
<img width="1919" height="333" alt="image" src="https://github.com/user-attachments/assets/330a4a0b-dbcc-4632-aeb7-ac3225144424" />

- ### 6.3. Check and Diff Modes

**Purpose**: Provides a comprehensive view of the changes that would be made by the playbook.

```bash
    ansible-playbook -i inventory.ini playbook.yml --check --diff
```

<img width="1909" height="670" alt="Screenshot 2025-07-23 173512" src="https://github.com/user-attachments/assets/20f96703-637b-4a8a-84ef-663b4da909ef" />

---

## 7. Troubleshooting


| **Issue/Command**                        | **Resolution/Description**                                 |
|------------------------------------------|-------------------------------------------------------------|
| SSH permission denied                    | Check user and SSH key.                                     |
| Missing variables                        | Ensure all required variables are provided.                 |
| Vault decryption failed                  | Verify vault password file.                                 |
| `ansible-playbook site.yml -i inventory/prod.ini -vvv` | Run playbook with increased verbosity for debugging. |



---

## 8. Conclusion

This SOP provides a clear, structured approach to executing Ansible playbooks effectively. By following the outlined prerequisites, execution steps, and validation checks, users can ensure reliable and error-free automation across environments.


---

## 9. FAQs

#### 1.  How can I pass variables to a playbook at runtime?

You can use the -e or --extra-vars flag:
```bash
   ansible-playbook site.yml -e "env=prod version=1.2"
```

#### 2. How do I increase the verbosity of playbook output?

Use the -vvv flag
```bash
   ansible-playbook site.yml -i inventory -vvv
```

#### 3. How do I test a playbook without making changes?

Use the --check flag to run Ansible in dry run mode:
```bash
   ansible-playbook site.yml --check
```

---

## 10. Contact Information

| Name| Email Address      | GitHub | URL |
|-----|--------------------------|-------------|---------|
| Ishaan | ishaan.aggarwal.snaatak@mygurukulam.co|  Ishaan-Dev1  |   https://github.com/Ishaan-Dev1  |


---

## 11. References

| **Title**                                 | **Link**                                                                                      |
|-------------------------------------------|-----------------------------------------------------------------------------------------------|
| Ansible Playbooks – Official Documentation| [Visit](https://docs.ansible.com/ansible/latest/user_guide/playbooks.html)                    |
| Ansible Inventory – Official Guide        | [Visit](https://docs.ansible.com/ansible/latest/user_guide/intro_inventory.html)              |
| Passing Variables to Playbooks            | [Visit](https://docs.ansible.com/ansible/latest/user_guide/playbooks_variables.html)          |
| Best Practices for Ansible Playbooks      | [Visit](https://docs.ansible.com/ansible/latest/tips_tricks/index.html)                       |
















