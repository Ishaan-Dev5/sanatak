<img src="https://git-scm.com/images/logos/downloads/Git-Icon-1788C.png" alt="Git Logo" width="120"/>

# VCS Authorization Strategy

---

### Author Information

| **Author**   | **Created on** | **Version** | **Last updated by** | **Last edited on** | **Level** | **Reviewer**  |
|--------------|----------------|-------------|---------------------|--------------------|-----------|---------------|
| Ishaan    | 5-08-25    | v1.0  |  Ishaan  |5-08-25   | Internal    | Rohit Chopra    | 

---

## Table of Contents

1. [Introduction](#1-introduction)
2. [What are Branch Access Policies?](#2-what-are-branch-access-policies) 
3. [Why Branch Access Policies ](#3-why-branch-access-policies)  
4. [Branch Protection Rules](#4-branch-protection-rules)  
5. [Workflow](#5-workflow)
6. [Advantages](#6-advantages)  
7. [Disadvantages](#7-disadvantages)  
8. [Best Practices](#8-best-practices)  
9. [Conclusion](#9-conclusion)
10. [FAQs](#10-FAQs)  
11. [Contact Information](#11-contact-information)  
12. [References](#12-references)

---

## 1. What are Authorization Strategy

Version Control Systems (VCS) like Git, GitHub, GitLab, and Bitbucket help developers manage changes to code. A key part of keeping them secure is the authorization strategy, which controls who can access or change what. A clear strategy keeps the code safe, makes teams more accountable, and helps everyone work better together.


---

## Why Authorization Strategy Matters

Authorization is a core part of access control. While [**authentication**](https://github.com/Snaatak-Apt-Get-Swag/documentation/blob/SCRUM-102-mansoor/VCS/Security-Access/Authentication-Docs/README.md) verifies *who* a user is, **authorization** defines *what* that user can do. Without proper authorization strategies:

- Unauthorized users may access or modify sensitive code.
- Compliance and audit requirements may not be met.

A secure authorization strategy helps enforce the **principle of least privilege**, ensuring users have access only to the resources they need.

---

## Access Levels in VCS

Most VCS platforms provide role-based access control (RBAC) with common roles such as:

| Role        | Description                                                                 |
|-------------|-----------------------------------------------------------------------------|
| Admin       | Full control over repositories, user management, and settings.              |
| Maintainer  | Manage repository settings but limited in user/group-level control.         |
| Developer   | Can push code, manage issues, merge requests, and CI/CD pipelines.          |
| Reporter    | Read-only access to code, issues, and documentation.                        |
| Guest       | Minimal access, often limited to viewing public documentation or issues.    |


---


