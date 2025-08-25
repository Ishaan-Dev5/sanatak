
# Jenkins Assignment – User Authentication & Authorization

## Assignment Overview

This assignment covers user authentication and authorization using Jenkins. It is divided into two parts:

- **Part 1**: Role-Based Access Control (RBAC) using the Role-Based Authorization Strategy plugin.
- **Part 2**: Enabling Single Sign-On (SSO) for Admin using Google OAuth.

---

##  Part 1: Role-Based Access Control (RBAC)

###  Team Structure & Permissions


![Screenshot 2025-05-12 173022](https://github.com/user-attachments/assets/436ec48a-933c-4be4-8b53-81d2fac46e25)

---

###  Jenkins Jobs Created

A total of **9 dummy jobs** were created, each printing its job name and build number:

![Screenshot 2025-05-12 173144](https://github.com/user-attachments/assets/ac0e8aff-db26-4fbf-b94e-a84506887e0f)


- **Developer View**
  - `dev-1`
  - `dev-2`
  - `dev-3`


![Screenshot 2025-05-12 173100](https://github.com/user-attachments/assets/c66eb6e6-edd9-4ae1-849e-707aea9750dc)


- **Testing View**
  - `test-1`
  - `test-2`
  - `test-3`

    
![Screenshot 2025-05-12 173127](https://github.com/user-attachments/assets/d329fc7f-af8b-47f5-8f05-649f0d32d440)

- **DevOps View**
  - `devops-1`
  - `devops-2`
  - `devops-3`

![Screenshot 2025-05-12 173144](https://github.com/user-attachments/assets/5c41e0ae-3380-4688-812d-ea4ae7a780cf)

  

---

###  Users & Roles

| Role     | Users          |
|----------|----------------|
| Developer | `developer-1`, `developer-2` |
| Testing   | `testing-1`, `testing-2`     |
| DevOps    | `devops-1`, `devops-2`       |
| Admin     | `admin-1`                    |



![Screenshot 2025-05-12 173005](https://github.com/user-attachments/assets/017fa37e-a89d-4725-8e8b-72d5701b3453)

![Screenshot 2025-05-12 173022](https://github.com/user-attachments/assets/1d5786fc-3afa-4a69-a0f5-b0c8e74a08c6)


---

###  Authorization Strategy Used

- **Strategy**: **Role-Based Authorization Strategy**
- **Plugin**: `Role-based Authorization Strategy Plugin`
- **Implementation**:
  - Created global roles: `developer`, `tester`, `devops`, `admin`
  - Assigned job-specific permissions to roles
  - Mapped users to respective roles
  - Created views using **Nested View Plugin** for clean separation

    

---

![Screenshot 2025-05-12 173033](https://github.com/user-attachments/assets/4f907712-c0d9-463b-b4cc-0fc675f305cb)







##  Part 2: SSO with Google for Admin

###  Features

- Google Single Sign-On (SSO) integration for admin access
- OAuth credentials configured via Google Developer Console
- Restricted to `admin-1` using Google login

---

###  Configuration Steps

1. **Google OAuth Setup**:
   - Created project in Google Developer Console
   - Enabled **Google+ API**
   - Created **OAuth 2.0 credentials**
   - Whitelisted redirect URI from Jenkins

2. **Jenkins Setup**:
   - Installed `Google Login Plugin`
   - Configured `client ID` and `client secret`
   - Enabled security: Google SSO + Role-Based Strategy
   - Mapped `admin-1` to `admin` role upon login

---

![Screenshot 2025-05-13 155700](https://github.com/user-attachments/assets/4bb06bde-6f86-49c1-880e-0f97705e6902)
![Screenshot 2025-05-13 155743](https://github.com/user-attachments/assets/265a7b6b-4f1b-4c83-96c7-899de38337e8)


---

##  Tools & Plugins Used

- Jenkins
- Role-based Authorization Strategy Plugin
- Google Login Plugin





