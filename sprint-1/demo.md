# GitHub Role-Based Access Control (RBAC) for Organisations

## 1. Introduction
Role-Based Access Control (RBAC) in GitHub allows organisations to manage who can perform certain actions at both the **organisation** and **repository** levels.  
This helps ensure security, proper governance, and clear separation of responsibilities.

---

## 2. Organisation Roles

### 2.1 Available Organisation Roles
| Role            | Description |
|-----------------|-------------|
| **Owner**       | Full administrative access to the organisation, repositories, teams, billing, and security settings. |
| **Member**      | Default role with limited privileges, can be given repository access via teams or direct assignment. |
| **Billing Manager** | Manages billing settings only, no access to code or repository settings. |

---

### 2.2 How to Assign Organisation Roles
1. Go to your **GitHub Organisation Settings**.
2. Navigate to **People**.
3. Search for the user and click on their role dropdown.
4. Select **Owner**, **Member**, or **Billing Manager**.

**Example Screenshot:**
![Organisation Roles](./86695659-be1d-474f-a884-cbd617f9a529.png)

---

## 3. Creating Teams in an Organisation

### 3.1 Why Use Teams?
- Easier permission management.
- Apply the same access level to multiple members at once.
- Organise members by function (e.g., DevOps, QA, Backend).

### 3.2 Steps to Create a Team
1. In your organisation, go to the **Teams** section.
2. Click **New Team**.
3. Enter a team name and description.
4. Set **Parent Team** (optional, for nested team structure).
5. Choose team visibility (**Secret** or **Visible**).
6. Click **Create Team**.

**Example Screenshot:**
![Create Team](./37c775d3-7ae0-46a0-acaa-385d0c81e00a.png)

---

## 4. Assigning a Repository to a Team

### 4.1 Steps:
1. Open the created team.
2. Go to **Repositories** tab.
3. Click **Add a repository**.
4. Select the desired repository.
5. Assign the **Repository Role** (Read, Write, Maintain, Admin).

**Example Screenshot:**
![Assign Repo to Team](./c3c74f10-a3c1-48d9-b614-e60d5de4937d.png)

---

## 5. Repository Roles and Permissions

| Repo Role  | Permissions |
|------------|-------------|
| **Read**   | Clone repository, open issues, view pull requests, view code, and pull updates. |
| **Triage** | Read access + manage issues and pull requests without write access to the code. |
| **Write**  | Read + push commits, manage issues and pull requests. |
| **Maintain** | Write + manage repository settings except sensitive/security settings. |
| **Admin**  | Full control, including repository deletion, access management, and security settings. |

**Example Screenshot:**
![Repo Roles](./060d6348-b1d2-40df-a0d6-e8b93585392a.png)

---

## 6. Best Practices for GitHub RBAC
- **Principle of Least Privilege** – Assign the lowest role required for a member’s task.
- **Use Teams** – Avoid assigning permissions directly to individuals.
- **Regular Access Review** – Audit team and repository permissions periodically.
- **Separate Duties** – Avoid giving the same person both code write access and deployment access unless necessary.
- **Limit Owner Role** – Keep the number of owners minimal.

---

## 7. References
- [GitHub Docs – Managing Organisation Roles](https://docs.github.com/en/organizations/managing-peoples-access-to-your-organization-with-roles)
- [GitHub Docs – Repository Permission Levels](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/managing-repository-settings/repository-permission-levels-for-an-organization)
- [GitHub Docs – Creating Teams](https://docs.github.com/en/organizations/organizing-members-into-teams/creating-a-team)

---
