
<img width="860" height="277" alt="1586766458581" src="https://github.com/user-attachments/assets/3d9b5d52-156d-49fa-a89c-1c427840585c" />


# POC of REACT DAST

---

## Author Information


| **Author**   | **Created on** | **Version** | **Last updated by** | **Last edited on** | **Level** | **Reviewer**  |
|--------------|----------------|-------------|---------------------|--------------------|-----------|---------------|
| Ishaan    | 17-08-25    | v1.0  |  Ishaan  |17-08-25   | Internal    | Rohit Chopra    | 
| Ishaan    |     |   |  Ishaan  |   | L0    |     | 
| Ishaan    |     | v1.0  |  Ishaan  |15-08-25   | L1    |     | 
| Ishaan    |     | v1.0  |  Ishaan  |15-08-25   | L2    |    | 

---

## Table of Contents

1. [Introduction](#1-introduction)
2. [Prerequisites](#2-prerequisites)
3. [System Requirements](#3-System-Requirements)
4. [Setup and Execution](#4-Setup-and-Execution)
5. [Troubleshooting](#5-troubleshooting)
6. [FAQs](#6-FAQs)
7. [Contact Information](#7-contact-Information)
8. [References](#8-references)


---

## 1. Introduction

This document provides a Proof of Concept (POC) for implementing 

---

## 2. Prerequisites



- **Java 11+** installed (`sudo apt install openjdk-17-jdk`)  
- **React app or target application running** for scanning  


---
## 3. System Requirements

| **Requirement** | **Minimum**          | **Recommended**      |
|-----------------|--------------------|--------------------|
| **OS**          | Ubuntu 20.04+       | Ubuntu 22.04+       |
| **CPU**         | 2 cores             | 4 cores or more     |
| **RAM**         | 2 GB                | 4 GB or more        |
| **Disk Space**  | 500 MB              | 1 GB or more        |
| **Ports**       | Any free port (default: 8080) | 8080 or custom free port |

---


## 4. Setup and Execution

### Step 1: Install Java 

```bash
 sudo apt update
sudo apt install openjdk-17-jdk -y
```
<img width="1247" height="524" alt="image" src="https://github.com/user-attachments/assets/aadc74f4-3f7f-46fc-910b-52b3db58d1b5" />


---
### Step 2: Install Zap

```bash
sudo snap install zaproxy --classic

```
---

### Step 3: Start Zap
```bash
zaproxy

```
<img width="1907" height="814" alt="Screenshot 2025-08-18 004630" src="https://github.com/user-attachments/assets/8980231c-c7e7-471d-b5d3-b2ba5123a885" />

---
### Step 4: Click on Automated scan and enter the url 
<img width="1915" height="628" alt="image" src="https://github.com/user-attachments/assets/100c3345-d3c3-4299-b750-1533b0449eba" />

           


### Step 5: Click on Generate Report

<img width="788" height="699" alt="image" src="https://github.com/user-attachments/assets/d068df51-c5b0-41c5-8bdb-89fa13a9cf25" />

---
### Step 6: Access the report

<img width="880" height="868" alt="image" src="https://github.com/user-attachments/assets/b5050b51-e65f-4bb0-b26a-e6713ce38926" />


---

### Step 7. Analyze the alerts 
<img width="633" height="849" alt="image" src="https://github.com/user-attachments/assets/50c50dad-7b55-42e9-bc8d-3dbd6b97f400" />

---



## 5. Troubleshooting

| Issue                                  | Possible Cause                                         | Solution                                                                            |
| -------------------------------------- | ------------------------------------------------------ | ----------------------------------------------------------------------------------- |
| Java not found                         | Java not installed or PATH not set                     | Install JDK 11+ (`sudo apt install openjdk-17-jdk`) and verify with `java -version` |
| Target URL not reachable               | App not running or firewall blocking                   | Ensure your React app is running and ports are accessible                           |
| Scan fails in CI/CD pipeline           | Headless flags missing or network issues               | Use `-daemon -headless` and verify network connectivity in pipeline agent           |
| Reports not generated                  | Incorrect report path or permissions                   | Specify a valid output path with write permissions using `-report` option           |

---

## 6. FAQs


**1. Do I need a database for ZAP?**  
→ No, ZAP is standalone. Reports are generated locally and do not require a database.

**2. Can I scan a React app running locally?**  
→ Yes, you can scan any running app. Make sure the URL is accessible (e.g., `http://localhost:3000`).

**3. Which Java version is required?**  
→ ZAP requires Java 11+. OpenJDK 17 is recommended for newer versions.

**4. Can I integrate ZAP with Jenkins?**  
→ Yes, you can run ZAP scans in Jenkins pipelines using headless mode and generate reports automatically.

**5. How do I access the scan report?**  
→ Reports can be exported as HTML, XML, or JSON from the ZAP GUI or CLI in headless mode.


---







## 7. Contact Information

| Name| Email Address      | GitHub | URL |
|-----|--------------------------|-------------|---------|
| Ishaan | ishaan.aggarwal.snaatak@mygurukulam.co|  Ishaan-Dev1  |   https://github.com/Ishaan-Dev1  |

---

## 8. References

| Resource |  Link |
|----------|------|
| **SonarQube Documentation** |  [Visit](https://docs.sonarqube.org/latest/) |

