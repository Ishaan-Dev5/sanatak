
<img src="https://git-scm.com/images/logos/downloads/Git-Icon-1788C.png" alt="Git Logo" width="120"/>

# Branch Access Policies Documentation

---

### Author Information

| **Author**   | **Created on** | **Version** | **Last updated by** | **Last edited on** | **Level** | **Reviewer**  |
|--------------|----------------|-------------|---------------------|--------------------|-----------|---------------|
| Ishaan    | 30-07-25    | v1.0  |  Ishaan  |30-07-25   | Internal    | Rohit Chopra    | 

---

## Table of Contents

1. [Introduction](#1-introduction)  
2. [Why Branch Access Policies ](#2-why-branch-access-policies)  
3. [Branch Protection Rules](#3-branch-protection-rules)  
4. [Access Policies](#4-access-policies)  
5. [Workflow Controls](#5-workflow-controls)  
6. [Advantages](#6-advantages)  
7. [Disadvantages](#7-disadvantages)  
8. [Best Practices](#8-best-practices)  
9. [Conclusion](#9-conclusion)  
10. [Contact Information](#10-contact-information)  
11. [References](#11-references)

---

## 1. Introduction

Branch access policies in GitHub, often referred to as branch protection rules or rulesets, are a set of configurations that repository administrators can implement to control how changes are made to specific branches within a repository.

---
## 2. What are Branch Access Policies 

Branch Access Policy is a set of rules that control who can make changes to specific branches in a GitHub repository and how those changes can be made.

Git branch protection rules are a powerful configuration option that enables repository administrators to enforce security policies. This helps protect the git branches from unexpected code commits or deletion by any unauthorized person(s) / user group(s).
Unrestricted branch access can lead to unreviewed code, broken builds, or security issues.

## 2. Why Branch Access Policies 



**Branch access policies help:**

- Avoid unnecessary code commits to the branch
- Enforce code reviews before merging the code to the branch
- Maintain a healthy codebase without affecting collaboration
- Maintain a commit history (by disallowing force pushes)
- Prevent code from leaking into your public repositories 

---

## 3. Branch Protection Rules

| Rule                            | Description                                                                 |
|----------------------------------|-----------------------------------------------------------------------------|
| **Require a pull request before merging**|      Prevents direct pushes — changes must go through a pull request.           |
| **Require status checks to pass before merging**      |     Ensures automated checks (like CI tests) pass before merging.                                      |
| **Require conversation resolution before merging**             |    All review comments and discussions must be resolved before merging.            |
| **Require signed commits**      |    Only commits with verified digital signatures are allowed.                 |
| **Require linear history**        |                           	Enforces a clean commit history — no merge commits |
| **Require deployments to succeed before merging**          |     	Code can only be merged if deployment to an environment is successful.  |   
|    **Lock branch**   |             Branch is read-only. Users cannot push to the branch    |

---



## 5. Workflow Controls

| Control Feature              | Description                                                               |
|------------------------------|---------------------------------------------------------------------------|
| **Linear History Requirement** | Prevents merge commits and enforces rebase workflow.                     |
| **Auto-Merge Settings**       | Allows merging PRs automatically once all checks pass.                    |
| **Draft Pull Requests**       | Allows work-in-progress PRs without triggering reviews or actions.        |
| **Lock Branch**               | Temporarily disables all changes to a branch.                             |

---

## 6. Advantages

| Benefit                       | Description                                                               |
|-------------------------------|---------------------------------------------------------------------------|
| **Improved Code Quality**     | Ensures peer review and automated checks are performed.                   |
| **Increased Security**        | Restricts who can make changes to critical branches.                      |
| **Stable Main Branch**        | Prevents breaking changes from entering production codebases.             |
| **Audit Trail**               | Keeps history of who made changes and who approved them.                  |

---

## 7. Disadvantages

| Drawback                      | Description                                                                 |
|-------------------------------|-----------------------------------------------------------------------------|
| **Initial Setup Complexity**  | Requires careful planning and configuration for teams and roles.           |
| **Reduced Flexibility**       | May slow down development in fast-paced teams if too strict.               |
| **Access Bottlenecks**        | Merges may be delayed if reviewers or approvers are unavailable.           |
| **Onboarding Overhead**       | New team members need to be trained on protected branch policies.          |

---

## 8. Best Practices

| Best Practice                    | Description                                                              |
|----------------------------------|--------------------------------------------------------------------------|
| **Protect Key Branches**         | Apply strict rules to `main`, `release`, and `production` branches.      |
| **Enforce Reviews**              | Require at least 1–2 reviewers for every pull request.                   |
| **Use Status Checks**            | Integrate CI/CD pipelines with branch protection.                        |
| **Restrict Write Access**        | Allow direct push only for automation or authorized users.               |
| **Document Policies Clearly**    | Make policies visible and understandable to all contributors.            |
| **Enable Required Commit Signing** | Add commit verification via GPG for authenticity.                      |

---

## 9. Conclusion

Branch access policies are essential for maintaining a secure, high-quality, and collaborative development environment. They reduce the risk of errors, enforce process discipline, and ensure teams deliver reliable code to production.

 **Recommended Practice:** Protect the `main` and `release` branches with enforced PR reviews, CI status checks, and restricted write access for all team projects.

---

## 10. Contact Information

| Name| Email Address      | GitHub | URL |
|-----|--------------------------|-------------|---------|
| Ishaan | ishaan.aggarwal.snaatak@mygurukulam.co|  Ishaan-Dev1  |   https://github.com/Ishaan-Dev1  |


---

## 11. References

| Source                          | Link                                                                 |
|---------------------------------|----------------------------------------------------------------------|
| Setup git protection rules | [Link](https://spectralops.io/blog/how-to-set-up-git-branch-protection-rules/) |
---
