<img width="800" height="701" alt="image" src="https://github.com/user-attachments/assets/f32ddb1e-44a5-4182-b335-13c31d0fd2b3" />



# Full Stack Document 

---

### Author Information

| **Author**   | **Created on** | **Version** | **Last updated by** | **Last edited on** | **Level** | **Reviewer**  |
|--------------|----------------|-------------|---------------------|--------------------|-----------|---------------|
| Ishaan    | 5-08-25    | v1.0  |  Ishaan  |5-08-25   | Internal    | Rohit Chopra    | 

---

## Table of Contents

1. [Introduction](#1-introduction)
2. [](#2) 
3. [s ](#)
4. [Different Authorization Strategies](#)
5. [Access Levels in VCS](#)  
6. [Audit Trails](#)
7. [Integration with Identity Providers](#)  
8. [Advantages](#)  
9. [Disadvantages](#)  
10. [Best Practices](#)
11. [Conclusion)  
12. [FAQs](#1s)
13. [Contact Information](#) 
14. [References](#)

---

# 1. Introduction



---

# 2. Purpose


---

## Pre-requisites

The Full Stack API application has dependencies on other REST APIs from **[OT-Microservices](https://github.com/OT-MICROSERVICES)**. To run the application successfully, ensure the following APIs are configured and running:

* **[Employee API](https://github.com/Snaatak-Apt-Get-Swag/documentation/blob/SCRUM-73-kawalpreet/OT-Microservices/Applications/Employee-API/Introduction/README.md)**
* **[Attendance API](https://github.com/Snaatak-Apt-Get-Swag/documentation/blob/SCRUM-71-mansoor/OT-Microservices/Applications/Attendance-API/Introduction/README.md)**
* **[Salary API](https://github.com/Snaatak-Apt-Get-Swag/documentation/blob/SCRUM-75-mansoor/OT-Microservices/Applications/Salary-API/Introduction/README.md)**
* **[Frontend API](https://github.com/Snaatak-Apt-Get-Swag/documentation/blob/scrum-77-sunny/OT-Microservices/Frontend-api/Introduction/README.md)**

---

# System Requirements

| Requirement   | Details                      |
|---------------|-----------------------------|
| **OS**        | Ubuntu or other Linux-based OS |
| **RAM**       | 4 GB minimum                |
| **Disk Space**| 40 GB                       |
| **Processor** | Dual-core recommended       |
| **Instance**  | t2.large                    |

---

## Dependencies
### Build time Dependency
| Name           | Version | Description        |
|----------------|---------|--------------------|
| `<application>` | `<version>` | `<Description>` |
| `<application>` | `<version>` | `<Description>` |

###  Run time Dependency
| Name           | Version    | Description        |
| -------------- | ---------- | ------------------ |
| `<application>` | `<version>`| `<Description>`   |
| `<application>` | `<version>`| `<Description>`   |

### Other Dependency
| Name           | Version    | Description        |
| -------------- | ---------- | ------------------ |
| `<application>` | `<version>`| `<Description>`   |
| `<application>` | `<version>`| `<Description>`   |



---
# Ports

| Port  | Protocol/Service  | Description                                         |
|-------|-------------------|-----------------------------------------------------|
| 8080  | HTTP (Swagger UI) | Access Swagger UI for API documentation             |
| 9042  | ScyllaDB          | Default port for ScyllaDB NoSQL database            |
| 6379  | Redis             | Default port for Redis cache                        |
| 80    | HTTP              | Standard web traffic                                |
| 443   | HTTPS             | Secure web traffic                                  |
|||

---

# Architecture

<img width="2912" height="1156" alt="frontend (1)" src="https://github.com/user-attachments/assets/357cc233-d73c-4615-b625-e35342c782e9" />

---


# API Setup and Execution

## Setup Backend and Frontend API

| API Name       | Link                                                                                                                                                                   |
| -------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Employee API   | [Configure Employee API](https://github.com/Snaatak-Cloudops-Crew/documentation/blob/SCRUM-67-Sneha-Joshi/OT-Microservices/Applications/Employee-API/POC/README.md)            |
| Attendance API | [Configure Attendance API](https://github.com/Snaatak-Cloudops-Crew/documentation/blob/scrum-7-aryan-mishra/OT-Microservices/Applications/Attendance-Api/Introduction/README.md) |
| Salary API     | [Configure Salary API](https://github.com/Snaatak-Cloudops-Crew/documentation/tree/e64036f22062fc2620205cbcfbba243c15db701f/OT-Microservices/Applications/Salary-API/POC)    |
| Frontend API   | [Configure Frontend API](https://github.com/Snaatak-Cloudops-Crew/documentation/blob/SCRUM-71-Ashutosh/OT-Microservices/Applications/frontend-api/POC/README.md)               |



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

