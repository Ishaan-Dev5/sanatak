# GO DAST: Dynamic Application Security Testing for Go Applications

<img width="400" height="373" alt="image" src="https://github.com/user-attachments/assets/280157e6-597c-47a4-a5e5-0d812bb05702" />

---

## Author Information

| Author   | Created on | Version | Last updated by | Last edited on | Level   | Reviewer      |
|----------|------------|---------|-----------------|----------------|---------|--------------|
| Ishaan   | 17-08-25   | v1.1    | Ishaan          | 25-08-17       | Internal| Rohit Chopra |

---

## Table of Contents

1. [Introduction](#1-introduction)
2. [What is DAST?](#2-what-is-dast)
3. [Why DAST for Go?](#3-why-dast-for-go)
4. [DAST Workflow](#4-dast-workflow)
5. [Popular DAST Tools](#5-popular-dast-tools)
6. [Go-Specific Guidance](#6-go-specific-guidance)
7. [Comparison Table](#7-comparison-table)
8. [Advantages](#8-advantages)
9. [Disadvantages](#9-disadvantages)
10. [Proof of Concept (POC)](#10-proof-of-concept-poc)
11. [Best Practices](#11-best-practices)
12. [Conclusion](#12-conclusion)
13. [FAQs](#13-faqs)
14. [Contact Information](#14-contact-information)
15. [References](#15-references)

---

## 1. Introduction

This document provides a comprehensive overview of **Dynamic Application Security Testing (DAST)**, with practical guidance for Go web/API applications. DAST tests running apps for vulnerabilities by simulating real-world attacks, making it vital for modern Go projects.

---

## 2. What is DAST?

DAST is a black-box security technique that scans live applications for vulnerabilities (e.g., XSS, SQL injection, auth flaws) without needing source code. It interacts with the exposed endpoints (web, API) and analyzes their behavior under attack-like conditions.

---

## 3. Why DAST for Go?

- **Go’s web ecosystem** (Gin, Echo, Fiber, net/http, gRPC) is widely adopted for its speed, but security flaws can still exist.
- DAST works independently of language, but Go apps may have unique patterns (e.g., custom middleware, REST/gRPC APIs) that require attention.
- Go’s static binaries may hide vulnerabilities until runtime—DAST helps uncover these real-world issues.

**Example vulnerabilities in Go apps:**
- Insecure JWT/OAuth implementations
- Mishandled session cookies
- Unvalidated input in API endpoints
- Missing security headers
- Directory traversal in static file servers

---

## 4. DAST Workflow

```mermaid
flowchart TD
    A[App Deployment (Go)] --> B[DAST Tool Scan]
    B --> C{Vulnerabilities Found?}
    C -->|Yes| D[Report & Notify]
    D --> E[Developer Fixes]
    E --> A
    C -->|No| F[Continue Dev/Release]
```

---

## 5. Popular DAST Tools

| Tool           | Notes for Go Projects |
|----------------|----------------------|
| **OWASP ZAP**  | Free, supports REST APIs, Docker; can use OpenAPI specs from Go code (Swagger). |
| **Burp Suite** | Powerful, manual & automated; good for custom Go endpoints, supports API scanning. |
| **StackHawk**  | Dev-focused, CI/CD integration; built for modern apps, supports Go APIs via OpenAPI. |
| **Invicti**    | Commercial, accurate scanning, supports OAuth/JWT—useful for Go auth flows. |
| **Acunetix**   | Comprehensive, strong SPA/API scanning; works well with Go web servers. |
| **Detectify**  | SaaS, plug-and-play; good for public-facing Go sites. |
| **Probely**    | API-first, excellent for Go microservices and continuous testing. |
| **GitLab DAST**| CI/CD native, works with Dockerized Go apps, based on ZAP. |

---

## 6. Go-Specific Guidance

### A. Integrating DAST with Go CI/CD

- Use Docker images for scanners (ZAP, StackHawk, GitLab DAST) in Go build pipelines (GitHub Actions, GitLab CI).
- Example GitHub Action for ZAP:
    ```yaml
    - name: DAST Scan
      uses: zaproxy/action-baseline@v0.8.0
      with:
        target: 'http://localhost:8080'
        rules_file_name: '.zap-rules'
    ```

### B. API Scanning

- Generate OpenAPI (Swagger) specs for Go apps with [swaggo/swag](https://github.com/swaggo/swag) or [go-swagger](https://github.com/go-swagger/go-swagger).
- Pass these specs to DAST tools for deep API testing.

### C. Authentication

- Configure scanners with JWT/OAuth tokens using Go’s `auth` libraries or custom login scripts.
- Use test user roles and realistic data for full coverage.

### D. Sample Vulnerable Go App

- See [bkimminich/juice-shop](https://github.com/bkimminich/juice-shop) or [gin-gonic/examples](https://github.com/gin-gonic/examples) for demo targets.

---

## 7. Comparison Table

| Tool        | License         | SPA/API | Auth Support | CI/CD | Go Integration | Ease of Use   |
|-------------|-----------------|---------|--------------|-------|---------------|---------------|
| ZAP         | OSS/Free        | Yes     | Yes (script) | Good  | Docker, API   | Moderate      |
| Burp Suite  | Commercial      | Yes     | Yes          | Good  | Manual/API    | Advanced      |
| StackHawk   | Commercial      | Yes     | Yes          | Excellent | API, OIDC   | Easy          |
| Invicti     | Commercial      | Yes     | Yes          | Very Good | API         | Easy          |
| Acunetix    | Commercial      | Yes     | Yes          | Very Good | API         | Easy          |
| Detectify   | SaaS            | Yes     | Limited      | Very Good | Web         | Very Easy     |
| Probely     | SaaS            | Yes     | Yes          | Very Good | API         | Easy          |
| GitLab DAST | OSS w/GitLab    | Yes     | Yes (ZAP)    | Excellent | Docker      | Moderate      |

---

## 8. Advantages

- Real-world testing, language agnostic
- No source code required
- Detects runtime issues (Go error handling, session flaws)
- OWASP Top 10 coverage (common Go vulnerabilities)
- Integrates with CI/CD
- Cost-effective, compliance support

---

## 9. Disadvantages

- No code insight (may miss Go-specific logic bugs)
- False positives/negatives
- Needs running Go app (staging environment)
- Auth complexity (especially custom Go flows)
- Scan times can be long
- Limited on business logic flaws
- Can be blocked by WAF/rate limits
- May miss unlinked API endpoints

---

## 10. Proof of Concept (POC)

**Setup Guide Example:**  
- [Go API App + OWASP ZAP in GitHub Actions](https://github.com/zaproxy/zaproxy/blob/main/.github/workflows/action-baseline.yml)
- [Generate OpenAPI from Go](https://github.com/swaggo/swag)

---

## 11. Best Practices

| Practice                        | Details |
|----------------------------------|--------|
| Staging/Test Environment         | Avoid production scans; use realistic test data. |
| CI/CD Integration               | Automate after deploy/test; include auth endpoints. |
| Proper Authentication           | Use login scripts/JWT/OAuth tokens, test all roles. |
| API Coverage                    | Supply OpenAPI for Go APIs; crawl JS-heavy SPAs. |
| Whitelist Scanner IPs           | Prevent WAF/rate-limit blocking. |
| Baseline + Full Scans           | Quick checks, then full deep scans. |
| Tune Payloads                   | Customize for Go stack; filter out static assets, health checks. |
| Prioritize Findings             | Focus on critical issues, manually validate. |
| Regular Scans                   | After major releases, dependency updates. |
| Combine with SAST/SCA           | Cover code-level and dependency vulnerabilities. |

---

## 12. Conclusion

DAST is essential for securing Go applications in real-world scenarios. With proper configuration and integration, it provides actionable insights on vulnerabilities—especially when combined with code/static analysis tools.

---

## 13. FAQs

### Do I need Go source code for DAST?
No. DAST only needs the running app and its endpoints.

### Can DAST test Go APIs?
Yes, especially with OpenAPI specs generated by Go tools.

### How does DAST handle Go authentication?
Most tools allow custom scripts or tokens; configure for your Go app’s auth mechanism.

### Can DAST detect Go-specific vulnerabilities?
DAST finds runtime/exploitable flaws; combine with SAST for Go code-level issues.

### Should DAST run in production?
No. Use staging/test environments.

### Can DAST be automated for Go CI/CD?
Yes. Most tools support Docker/GitHub Actions/GitLab CI for Go projects.

---

## 14. Contact Information

| Name   | Email                                 | GitHub         | URL                           |
|--------|---------------------------------------|----------------|-------------------------------|
| Ishaan | ishaan.aggarwal.snaatak@mygurukulam.co| Ishaan-Dev1    | https://github.com/Ishaan-Dev1|

---

## 15. References

| Resource      | Link |
|---------------|------|
| What is DAST? | [IBM: Dynamic Application Security Testing](https://www.ibm.com/think/topics/dynamic-application-security-testing) |
| Swaggo        | [Generate OpenAPI for Go](https://github.com/swaggo/swag) |
| ZAP Docs      | [OWASP ZAP](https://www.zaproxy.org/docs/) |
| StackHawk     | [StackHawk Docs](https://docs.stackhawk.com/) |
