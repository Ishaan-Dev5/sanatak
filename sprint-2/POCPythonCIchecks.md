

# POC OF python CI Checks – Static Code Analysis

## Author Information

| Last Updated On | Version | Author           | Level           | Reviewer               |
|-----------------|---------|------------------|-----------------|------------------------|
| 13-08-2025      | V1.1    |  Sunny Kumar | Internal Review | Aman Raj                 |
|                 |       | Sunny Kumar  | L0              | Shikha Tripathi        |
|                 |         | Sunny Kumar  | L1              | Kirti Nehra            |
|                 |         | Sunny Kumar  | L2              | Ashwini Singh/Deepak Nishad |


---

## Table of Contents

1. [Introduction](#introduction)
2. [Prerequisites](#prerequisites)
3. [System Requirements](#System-Requirements)
4. [Procedure](#procedure)
    - [Step 1: Update System Packages](#step-1-update-system-packages)
    - [Step 2: Check Existing Python Installation](#step-2-check-existing-Python-installation)
    - [Step 3: Install Pyhton](#step-3-install-Python)
    - [Step 4: Verify Installation](#step-4-verify-installation)
5. [Notes](#notes)
6. [Conclusion](#conclusion)
7. [FAQ](#FAQ)
8. [Contact Information](#contact-Information)
9. [References](#references)


---

## 1. Introduction

This guide outlines a simple workflow to perform Static Code Analysis for React applications using SonarQube. This ensures code quality, detects potential bugs, and enforces coding standards before integration, improving maintainability and reducing technical debt.

---
## Prerequisites

| Dependency            | Version                   |
| --------------------- | ------------------------- |
| **Node.js**           | v12.22.9                  |
| **npm**               | v8.5.1                    |
| **Java**              | JDK 11+                   |
| **Make**              | v4.3                      |
| **SonarQube**         | v9.x or above             |
| **SonarQube Scanner** | Latest compatible version |

---
## System Requirements

| Hardware/Software | Minimum Recommendation                     |
| ----------------- | ------------------------------------------ |
| **Processor**     | 2 CPU cores                                |
| **RAM**           | 4 GiB                                      |
| **Disk**          | 10 GB                                      |
| **OS**            | Ubuntu 22.04 LTS / Windows 10+ / macOS 11+ |

---


## Procedure

### Step 1: Update System Packages

```bash
sudo apt update && sudo apt upgrade -y
```

---
### Step 2: Install java and verify

```bash
sudo apt install openjdk-17-jdk -y
java -version
```

---
### Step 3: Create a SonarQube User

```bash
sudo adduser --system --no-create-home --group --disabled-login sonarqube
```
<img width="1147" height="184" alt="image" src="https://github.com/user-attachments/assets/00ca0b6a-e266-454e-920d-ea43c3ffd6ee" />

---
### Step 4: Install SonarQube

```bash
wget https://binaries.sonarsource.com/Distribution/sonarqube/sonarqube-10.5.1.90531.zip
sudo apt install unzip -y
unzip sonarqube-10.5.1.90531.zip
sudo mv sonarqube-10.5.1.90531 /opt/sonarqube
sudo chown -R sonarqube:sonarqube /opt/sonarqube

```
---
### Step 5: Create Systemd Service File

```bash
sudo nano /etc/systemd/system/sonarqube.service
```
and paste these line 

```bash
[Unit]
Description=SonarQube service
After=syslog.target network.target

[Service]
Type=forking
User=sonarqube
Group=sonarqube
ExecStart=/opt/sonarqube/bin/linux-x86-64/sonar.sh start
ExecStop=/opt/sonarqube/bin/linux-x86-64/sonar.sh stop
LimitNOFILE=65536
Restart=always

[Install]
WantedBy=multi-user.target
```
---
### Step 6: Reload, Enable & start the Service

```bash
sudo systemctl daemon-reload
sudo systemctl enable sonarqube
sudo systemctl start sonarqube
```

---
### Step 7: Access the Dashboard

```bash
http://<INSTANCE_PUBLIC_IP>:9000
```
with the help of `username : admin ` and `password : admin`

---

### Step 8: Create a Project in SonarQube

1. Go to **Projects** → **Create Project**  
2. Select **Manually**  
3. Enter:  
   - **Project Key** → `react-ci-poc`  
   - **Project Name** → `React CI POC`  
4. Choose **Locally**  
5. Generate a **Token** → copy it (we will need it in config)

---
### Step 9: Install SonarScanner

```bash
wget https://binaries.sonarsource.com/Distribution/sonar-scanner-cli/sonar-scanner-cli-5.0.1.3006-linux.zip
unzip sonar-scanner-cli-5.0.1.3006-linux.zip
sudo mv sonar-scanner-5.0.1.3006-linux /opt/sonar-scanner
echo 'export PATH=$PATH:/opt/sonar-scanner/bin' >> ~/.bashrc
source ~/.bashrc
```

and verify :

```
sonar-scanner --version
```
---

### Step 10: Clone the project repo and navigate into it

```bash
git clone <url>
cd directory
```
---
### Step 11: Configure Your React Project

Inside your React project root, create a file:
```
touch sonar-project.properties
```
and paste these line:

```bash
sonar-scanner \
  -Dsonar.projectKey=frontend \
  -Dsonar.sources=src \
  -Dsonar.host.url=http://<SONARQUBE_URL> \
  -Dsonar.login=sqp_edeca9095551edb1cb346522bd5554d49fd2a54c

```
---
### Step 12: Configure Your React Project


## FAQ



---
##  Conclusion

Integrating static code analysis into a React CI pipeline ensures that only clean, secure, and maintainable code reaches production. By using tools like ESLint, Prettier, and SonarQube, teams can enforce consistent coding standards, catch issues early, and reduce technical debt, ultimately improving code quality and development efficiency.

---




##  Contact Information

| Name             | Email                                         |
|------------------|-----------------------------------------------|
| Sunny Kumar  | sunny.kumar.snaatak@mygurukulam.co        |

---

##  References

| Resource | Description | Link |
|----------|-------------|------|
| **ESLint Documentation** | Official documentation for ESLint rules, setup, and usage. | [Visit](https://eslint.org/docs/latest/) |
| **Prettier Documentation** | Official guide for Prettier code formatting tool. | [Visit](https://prettier.io/docs/en/) |
| **SonarQube Documentation** | Documentation for SonarQube code quality and security analysis. | [Visit](https://docs.sonarqube.org/latest/) |
| **Stylelint Documentation** | Official documentation for Stylelint CSS/SCSS linter. | [Visit](https://stylelint.io/) |
| **GitHub Actions** | Guide to automate workflows using GitHub Actions. | [Visit](https://docs.github.com/en/actions) |


---
