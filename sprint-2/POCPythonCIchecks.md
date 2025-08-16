<img width="341" height="213" alt="Screenshot 2025-08-13 193419" src="https://github.com/user-attachments/assets/388c288c-a662-4b57-8c03-1821ea3a3c5a" />

# POC OF python CI Checks – Static Code Analysis

---

## Author Information


| **Author**   | **Created on** | **Version** | **Last updated by** | **Last edited on** | **Level** | **Reviewer**  |
|--------------|----------------|-------------|---------------------|--------------------|-----------|---------------|
| Ishaan    | 15-08-25    | v1.0  |  Ishaan  |15-08-25   | Internal    | Rohit Chopra    | 
| Ishaan    |     |   |  Ishaan  |   | L0    |     | 
| Ishaan    |     | v1.0  |  Ishaan  |15-08-25   | L1    |     | 
| Ishaan    |     | v1.0  |  Ishaan  |15-08-25   | L2    |    | 

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



---
## Prerequisites

| Dependency            | Version                   |
| --------------------- | ------------------------- |
| **Java**              | JDK 11+                   |
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
sudo apt update 
```
<img width="1447" height="612" alt="Screenshot 2025-08-16 162620" src="https://github.com/user-attachments/assets/e002874b-a32d-469b-9db7-ecb859703478" />

---
### Step 2: Install java and verify

```bash
sudo apt install openjdk-17-jdk -y
java -version
```
<img width="1522" height="493" alt="Screenshot 2025-08-16 162628" src="https://github.com/user-attachments/assets/c0fb479f-c7f2-4f58-a0e3-1a0376c43a7d" />

---

### Step 3: Install SonarQube

```bash
wget https://binaries.sonarsource.com/Distribution/sonarqube/sonarqube-10.5.1.90531.zip
sudo apt install unzip -y
unzip sonarqube-10.5.1.90531.zip
mv sonarqube-10.5.1.90531 sonarqube

```
<img width="1917" height="298" alt="Screenshot 2025-08-16 162720" src="https://github.com/user-attachments/assets/4e89030b-dd21-4798-b5d0-18a1ce1544d6" />

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
ExecStart=/home/ubuntu/sonarqube/bin/linux-x86-64/sonar.sh start
ExecStop=/home/ubuntu/sonarqube/bin/linux-x86-64/sonar.sh stop
User=ubuntu
Group=ubuntu
Restart=always

[Install] WantedBy=multi-user.target
```
---
### Step 6: Reload, Enable & start the Service

```bash
sudo systemctl daemon-reload
sudo systemctl start sonarqube
sudo systemctl enable sonarqube
```
<img width="1918" height="470" alt="Screenshot 2025-08-16 162738" src="https://github.com/user-attachments/assets/23a87118-b2eb-428b-abdf-d9838e1482bb" />

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
   - **Project Key** → `python`  
   - **Project Name** → `python`  
4. Choose **Locally**

<img width="1919" height="607" alt="Screenshot 2025-08-16 162914" src="https://github.com/user-attachments/assets/43989c71-ed43-448d-ae2a-44dc9b263ebc" />
 
5. Generate a **Token** → copy it (we will need it in config)

   <img width="1846" height="656" alt="Screenshot 2025-08-16 162933" src="https://github.com/user-attachments/assets/f032f656-dd75-4f4e-96ef-1f3fddc115d5" />


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
