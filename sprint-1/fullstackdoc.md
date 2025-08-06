
<img width="300" height="400" alt="image" src="https://github.com/user-attachments/assets/518f6847-6dca-4ffc-b8b7-6735b62adb64" />


# Full Stack Document 

---

### Author Information

| **Author**   | **Created on** | **Version** | **Last updated by** | **Last edited on** | **Level** | **Reviewer**  |
|--------------|----------------|-------------|---------------------|--------------------|-----------|---------------|
| Ishaan    | 6-08-25    | v1.0  |  Ishaan  |7-08-25   | Internal    | Rohit Chopra    | 

---

## Table of Contents

1. [Introduction](#1-introduction)
2. [](#2-what-is-authorization-strategy) 
3. [ ](#3-why-Authorization-Strategy-Matters)
4. [](#4-Different-Authorization-Strategies)
5. [](#5-Access-Levels-in-VCS)  
6. [](#6-Audit-Trails)
7. [](#7-Integration-with-Identity-Providers)  
8. [](#8-Advantages)  
9. [](#9-Disadvantages)  
10. [](#10-Best-Practices)
11. [](#11-Conclusion)  
12. [](#12-FAQs)
13. [Contact Information](#13-Contact-Information) 
14. [References](#14-references)

---
## 1. Introduction

This document outlines key authorization strategies in Version Control Systems (VCS) to ensure secure, role-based access to code. It covers access levels, audit trails, IdP integration, and best practices for managing permissions effectively.


---


## 2. What is Authorization Strategy

Version Control Systems (VCS) like Git, GitHub, GitLab, and Bitbucket help developers manage changes to code. A key part of keeping them secure is the authorization strategy, which controls who can access or change what. A clear strategy keeps the code safe, makes teams more accountable, and helps everyone work better together.


---

## 3. Why Authorization Strategy Matters

Authorization is a core part of access control. While [**authentication**](https://github.com/Snaatak-Apt-Get-Swag/documentation/blob/SCRUM-102-mansoor/VCS/Security-Access/Authentication-Docs/README.md) verifies *who* a user is, **authorization** defines *what* that user can do. Without proper authorization strategies:

- Unauthorized users may access or modify sensitive code.
- Compliance and audit requirements may not be met.

A secure authorization strategy helps enforce the **principle of least privilege**, ensuring users have access only to the resources they need.

---

## 4. Different Authorization Strategies:

#### 1. Personal Access Tokens (PATs)
| Attribute           | Description                                                                                   |
|---------------------|-----------------------------------------------------------------------------------------------|
| **Purpose**         | Authenticate users to GitHub APIs and the command line.                                       |
| **Scope & Permissions** | PATs can be fine-grained, granting access to specific repositories or actions (like read/write on issues, code, or workflows). |
| **Usage**           | Replaces passwords for HTTPS Git operations and API requests.                                 |
| **Management**      | Users generate and manage their PATs; tokens can be revoked at any time.                      |
| **Security**        | Tokens should be kept secret and never shared or committed to code.                           |

<img width="1904" height="855" alt="Screenshot 2025-08-06 194314" src="https://github.com/user-attachments/assets/b328043d-0c36-4ca8-a6be-399f41b65e7c" />


#### 2. Role-Based Access Control (RBAC)
| Attribute          | Description                                                                                                                                                   |
|--------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Purpose**        | Assigns permissions to users based on their roles within an organization or repository.                                                                        |
| **Typical Roles**  | - **Owner:** Full administrative access to the organization and all repositories.<br>- **Admin:** Manage repository settings and teams.<br>- **Maintainer:** Manage teams or repositories but with some limits.<br>- **Member:** Standard access, usually restricted to specific repositories or actions.<br>- **Outside Collaborator:** Access to specific repositories without being an org member. |
| **Granularity**    | Roles can be set at the organization or repository level, and custom roles can be created for finer control.     


<img width="1901" height="827" alt="Screenshot 2025-08-06 193859" src="https://github.com/user-attachments/assets/349a9441-33dc-43e4-9830-cc8db0a5c606" />

#### 3. Organization-Based Authorization
| Attribute              | Description                                                                                                                                                                                                          |
|------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Purpose**            | Controls access and permissions across all repositories and resources within an organization.                                                                                                                        |
| **Organization Settings** | - **Repository Access:** Control who can read, write, or administer each repository.<br>- **Team-Based Access:** Create teams with custom access levels to groups of repositories.<br>- **SAML SSO:** Require authentication through an identity provider. |
| **Repository Visibility** | Private, internal, or public.                                                                                                                                                                                     |
| **Security Policies**  | Enforce 2FA, IP allow-lists, and secret scanning.                                                                                                                             |
| **Audit & Compliance** | Organizations can monitor activity, enforce policies, and review authorization logs.        |

<img width="1915" height="474" alt="Screenshot 2025-08-06 194514" src="https://github.com/user-attachments/assets/6dca9bfb-a4a4-4057-b99f-d1091cd277a6" />


---


## 5. Access Levels in VCS

The official GitHub repository access levels are:

| Access Level | Description                                                                                      |
|--------------|--------------------------------------------------------------------------------------------------|
| **Read**     | Can view and clone the repository, view issues and pull requests.                                |
| **Triage**   | Can manage issues and pull requests (label, assign, close/open) without code write access.       |
| **Write**    | Can push to branches, manage issues and pull requests.                                           |
| **Maintain** | Can manage repository settings (except sensitive/admin settings), perform some admin tasks.       |
| **Admin**    | Full control over the repository, including settings, collaborators, and deletion.               |

At the organization level, the roles are:

| Org Role          | Description                                                               |
|-------------------|---------------------------------------------------------------------------|
| **Member**        | Standard organization user, access based on repo-level permissions.        |
| **Owner**         | Full control over all organization settings and repositories.              |
| **Billing Manager** | Can manage billing, but not code or repo settings.                      |

---


##  6. Audit Trails

Audit trails are chronological records of system or user activities that provide a detailed history of who did what, when, where, and how within a system or platform.

| Audit Event Type               | Description                                                                 |
|-------------------------------|-----------------------------------------------------------------------------|
| Branch Creation/Deletion	   | 	Captures who created or deleted which branch and when                         |
| Permission or Role Changes     | Logs when user permissions or roles are modified.                          |
| Repository Changes             | Includes push, merge, delete, and other git-related changes.               |
| Merge Requests / Pull Requests | Tracks PR creation, reviewers, approvals, merge status    |
| User Activity Monitoring       | Records user actions during their session to support traceability.         |

Stored in:
- Git logs
- VCS platform logs (GitHub/GitLab)
- External SIEM tools (Splunk, ELK)


Audit logs are vital for:
- Meeting compliance requirements (e.g., SOC 2, ISO 27001)
- Detecting unusual or unauthorized behavior
- Root cause analysis of production issue

---

## 7. Integration with Identity Providers

Modern VCS platforms support integration with Identity Providers (IdPs) to centralize and streamline access management. Common protocols and services include:

| Protocol / Service  | Description                                               |
|---------------------|-----------------------------------------------------------|
| OAuth2              | Authorization framework used by GitHub, Google, etc.     |
| LDAP / Active Directory | Directory service used in enterprise environments.     |
| SSO (Single Sign-On)| One-click access via corporate credentials.              |

---

## 8. Advantages

| Advantage                                             | Description                                                                 |
|-------------------------------------------------------|-----------------------------------------------------------------------------|
| Enhanced Security                                     | Prevents unauthorized access and changes to code.                          |
|Enables Role-Based Team Structure                             |  Separate roles across devs, reviewers, and admins              |
| IdP/SSO Integration                                   | Streamlines access management across multiple systems.                     |

---

## 9. Disadvantages

| Disadvantage                                             | Description                                                                 |
|-------------------------------------------------------|-----------------------------------------------------------------------------|
| Configuration Complexity                                | Requires careful setup and management to avoid misconfigurations.          |
| Risk of Over-Permission                                 | Mistakes in role assignment can expose sensitive data.                      |
| External Dependency on IdPs                             | Downtime in SSO/IdP services can block access for all users.                |

---

## 10. Best Practices

| Practice                          | Description                             |
|-----------------------------------|-----------------------------------------|
|  Enforce MFA                    | Add another layer of security           |
|  Disable Direct Push to Main    | Use protected branches                  |
|  Enable Code Review Workflow    | Require approval before merge           |
|  Regularly Audit Access         | Remove stale or unused accounts         |
|  Use Personal Access Tokens     | For CLI usage instead of passwords      |
|  Monitor Audit Logs             | Regular review for anomalies            |

---

## 11. Conclusion

A well-designed **Authn & Authz** strategy in VCS ensures secure, auditable, and efficient collaboration.  
We recommend adopting **Role-Based Access Control (RBAC)** and **SSO** with audit logging for all production-level repositories.

---

## 12. FAQs

**Q1. What’s the difference between authentication and authorization?**  
Authentication confirms the user's identity. Authorization defines what that user can access or do.

**Q2. Can I use GitHub without an IdP?**  
Yes, but integrating with an Identity Provider improves security and centralized control.

**Q3. What happens if an SSO/IdP service is down?**  
Users may be temporarily blocked from accessing the VCS. Plan for backups or break-glass accounts.

---

## 13. Contact Information

| Name| Email Address      | GitHub | URL |
|-----|--------------------------|-------------|---------|
| Ishaan | ishaan.aggarwal.snaatak@mygurukulam.co|  Ishaan-Dev1  |   https://github.com/Ishaan-Dev1  |


---

## 14. References

| Resource                         |  Link                                                                 |
|--------------------------------|--------------------------------------------------------------------------------|
| Branch Access Policies |[Link](https://github.com/Snaatak-Apt-Get-Swag/documentation/blob/SCRUM-112-ishaan/VCS/VCS-Policies/Branch-Access-Policies/README.md) |
| Authentication Documentation  |[Link](https://github.com/Snaatak-Apt-Get-Swag/documentation/blob/SCRUM-102-mansoor/VCS/Security-Access/Authentication-Docs/README.md)  |

