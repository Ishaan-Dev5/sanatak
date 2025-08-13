<img width="430" height="159" alt="gitleaks-ci" src="https://github.com/user-attachments/assets/eada7ff1-5f8d-4074-b294-ed9e6c73e040" />

# GitLeaks POC

---

## Author Information

| **Author**   | **Created on** | **Version** | **Last updated by** | **Last edited on** | **Level** | **Reviewer**  |
|--------------|----------------|-------------|---------------------|--------------------|-----------|---------------|
| Ishaan       | 11-08-25       | v1.0        | Ishaan              | 12-08-25           | Internal  | Rohit Chopra  | 

---

## Table of Contents

1. [Purpose](#1-purpose)  
2. [Pre-Requisites](#2-pre-requisites)  
3. [System Requirements](#3-system-requirements)
4. [Setup and Execution](#4-setup-and-execution)  
5. [Troubleshooting](#5-Troubleshooting)  
6. [Best Practices](#6-Best-Practices)  
7. [FAQs](#7-FAQs)   
8. [Contact Information](#8-contact-information)  
9. [References](#9-references)  

---

## 1. Purpose

This Proof of Concept (POC) demonstrates integrating Gitleaks, an open-source secret scanning tool, into a Jenkins CI pipeline.
The goal is to automatically scan source code for sensitive data (API keys, tokens, passwords) during the Continuous Integration (CI) process and prevent them from entering the repository

---

## 2. Pre-Requisites

- Jenkins server installed and running
- Git installed 
- Gitleaks binary installed 
- Access to the Git repository to be scanned
- Basic understanding of Jenkins Pipeline syntax
- Port 8080 should be available

---

## 3. System Requirements

| **Hardware/Software** | **Minimum Requirement** |
| --------------------- | ----------------------- |
| Processor             | 1 CPU (t2.micro EC2)    |
| RAM                   | 1 GiB                   |
| Disk                  | 8 GB                    |
| OS                    | Ubuntu 22.04 LTS        |
| Jenkins Version       | 2.516.1                  |
| Git                   | 2.34.1                   |

---

## 4. Setup and Execution

### 1. Fetch the latest Gitleaks version.

```bash
    GITLEAKS_VERSION=$(curl -s "https://api.github.com/repos/gitleaks/gitleaks/releases/latest" | grep -Po '"tag_name": "v\K[0-9.]+')
```



### 2. Download the Gitleaks binary

```bash
    wget -qO gitleaks.tar.gz https://github.com/gitleaks/gitleaks/releases/latest/download/gitleaks_${GITLEAKS_VERSION}_linux_x64.tar.gz
```


### 3. Extract the executable 

```bash
    sudo tar xf gitleaks.tar.gz -C /usr/local/bin gitleaks
```

### 4. verify the installation

```bash
    gitleaks version
```
<img width="1919" height="314" alt="image" src="https://github.com/user-attachments/assets/79ada9f9-ef69-4cf2-82a1-5fa1757124cf" />


### 5.  Create a Jenkins Pipeline Job

- Go to Jenkins Dashboard → New Item
- Select Pipeline
- Choose Pipeline script in configuration


<img width="1844" height="858" alt="Screenshot 2025-08-13 114157" src="https://github.com/user-attachments/assets/9e585ae6-6cc2-41bb-85a7-18f7e0aa1c78" />


### 6. Jenkins Pipeline Script

```groovy
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/OT-MICROSERVICES/employee-api.git'
            }
        }

        stage('Run Gitleaks Scan') {
            steps {
                sh '''
                echo "Running Gitleaks Secret Scan..."
                gitleaks detect --source . --report-format json --report-path gitleaks-report.json
                '''
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: 'gitleaks-report.json', onlyIfSuccessful: false
        }
        failure {
            echo "Secrets found! Please review gitleaks-report.json."
        }
    }
}

```

### 7. Execution and Review


- Run the Jenkins job.
- If secrets are detected:
  - The build will fail.
  - A gitleaks-report.json will be archived in Jenkins for review.
- If no secrets are found, the build will pass successfully

<img width="1919" height="862" alt="Screenshot 2025-08-13 114612" src="https://github.com/user-attachments/assets/48bfb59e-ed30-454f-a302-c223c77cb46e" />



---



## 5. Troubleshooting

| Issue                           | Solution                                                                              |
| ------------------------------- | ------------------------------------------------------------------------------------- |
| `gitleaks: command not found`   | Ensure Gitleaks binary is installed in `/usr/local/bin` and executable                |
| Job fails with permission error | Add execute permissions: `chmod +x /usr/local/bin/gitleaks`                           |
| Report file empty               | Check that the repository contains code to scan and that `--source .` path is correct |

---

## 6. Best Practices

- Run scans on Jenkins agents, not master nodes.
- Fail builds automatically if secrets are found in strict CI policies.
- Combine with git-secrets for defense in depth.

---




## 7. FAQs

#### 1. **Can Gitleaks run on Windows agents?**
Yes, download the Windows binary and update the path in the pipeline.

#### 2. **Does Gitleaks scan commit history?**
Yes, with the --no-git flag removed (default behavior scans git history).

---

## 8. Contact Information

| Name| Email Address      | GitHub | URL |
|-----|--------------------------|-------------|---------|
| Ishaan | ishaan.aggarwal.snaatak@mygurukulam.co|  Ishaan-Dev1  |   https://github.com/Ishaan-Dev1  |


---

## 9. References

| Description                       | Link                                                                 |
|------------------------------------|----------------------------------------------------------------------|
| Credential scanning document                       | [Link]()                         |
|  Gitleaks GitHub Repo | [Link](https://github.com/gitleaks/gitleaks) |
