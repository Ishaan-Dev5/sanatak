


<img width="860" height="277" alt="1586766458581" src="https://github.com/user-attachments/assets/3d9b5d52-156d-49fa-a89c-1c427840585c" />


# POC of GO DAST

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

This document provides a **Proof of Concept (POC)** for implementing **Dynamic Application Security Testing (DAST)** on a React application using **OWASP ZAP (Zed Attack Proxy)**.

---

## 2. Prerequisites


| Dependency                | Version / Notes                                                                                     |
| ------------------------- | --------------------------------------------------------------------------------------------------- |
| **Java**                  | JDK 17+                                                                                            |
| **OWASP ZAP**             | v2.16.1 or latest stable                                                                            |
| **Python3**               | 3.8+ (for zap-cli / zapcli)                                                                         |
| **zap-cli / zapcli**      | Latest from GitHub ([https://github.com/Grunny/zap-cli.git](https://github.com/Grunny/zap-cli.git)) |
| **pip**                   | Latest                                                                                              |
| **Browser / HTTP client** | For viewing scan reports                                                                            |




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

### Step 1: Install Java and pip

```bash
 sudo apt update
sudo apt install python3-apt python3-pip -y
sudo apt install openjdk-17-jdk -y

```
<img width="1648" height="362" alt="image" src="https://github.com/user-attachments/assets/20a53c1f-e976-423a-bf61-47b6fed3b433" />


---
### Step 2: Download and extract ZAP

```bash
wget https://github.com/zaproxy/zaproxy/releases/download/v2.16.1/ZAP_2.16.1_Linux.tar.gz
tar -xvzf ZAP_2.16.1_Linux.tar.gz
cd ZAP_2.16.1

```
<img width="1917" height="178" alt="image" src="https://github.com/user-attachments/assets/c7af9984-0dd8-4140-bf16-3d907eebbc03" />

---

### Step 3: Create Systemd Service File
```bash
sudo nano /etc/systemd/system/zap.service


```
and paste these line

```bash
[Unit]
Description=OWASP ZAP Daemon Service
After=network.target

[Service]
Type=simple
User=ubuntu
WorkingDirectory=/home/ubuntu/ZAP_2.16.1
ExecStart=/home/ubuntu/ZAP_2.16.1/zap.sh -daemon -host 0.0.0.0 -port 8080 -config api.disablekey=true
Restart=always
RestartSec=10
StandardOutput=journal
StandardError=journal

[Install]
WantedBy=multi-user.target

```


---

### Step 4 : Reload, Enable & start the Service

```bash
sudo systemctl daemon-reload
sudo systemctl enable zap.service
sudo systemctl start zap.service
sudo systemctl status zap.service


```

<img width="1917" height="446" alt="image" src="https://github.com/user-attachments/assets/341df366-c40a-4a98-b6dd-efad0b1d85cf" />
---
### Step 5: Create Python virtual environment for zap-cli
```bash
sudo apt install -y python3.10-venv
python3 -m venv ~/zap-env
source ~/zap-env/bin/activate
pip install --upgrade pip
pip install git+https://github.com/Grunny/zap-cli.git

```

---          


### Step 6: Verify ZAP daemon status


```bash
zap-cli -p 8080 status

```
<img width="982" height="75" alt="image" src="https://github.com/user-attachments/assets/fe928818-daf2-4004-b918-85e1278be045" />

---
### Step 7: Run Spider (Crawl) on GO app

```bash
zap-cli -p 8080 spider http://13.48.67.195:8080/swagger/index.html
```


---

### Step 8. Run Active Scan (Vulnerability Test) 

```bash
zap-cli -p 8080 active-scan http://13.48.67.195:8080/swagger/index.html
```
---
### Step 9. Generate HTML report
```bash
mkdir -p ~/zap_reports
zap-cli -p 8080 report -o ~/zap_reports/zap_report.html -f html
```
---
### Step 10. Serve the report on browser
```bash
cd ~/zap_reports
python3 -m http.server 8000
```
---
### Step 11: Web Dashboard

```
http://13.201.87.100:8000/zap_report.html
```

<img width="1891" height="576" alt="image" src="https://github.com/user-attachments/assets/52fee340-7b62-4eea-b08f-e42d7aa9384d" />
<img width="1763" height="359" alt="image" src="https://github.com/user-attachments/assets/110d1bf9-e36e-446b-a0da-7b03c70de884" />
<img width="1917" height="470" alt="image" src="https://github.com/user-attachments/assets/9e2addba-730c-4d2b-85ea-c0f2ff0e211b" />

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
| **DAST Document** |  [Visit]() |
