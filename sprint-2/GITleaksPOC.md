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
5. [Monitoring and Logging](#5-monitoring-and-logging)  
6. [Troubleshooting](#6-troubleshooting)  
7. [Disaster Recovery & High Availability](#7-disaster-recovery--high-availability)  
8. [FAQs](#8-faqs)  
9. [Contact Information](#9-contact-information)  
10. [References](#10-references)  

---

## 1. Purpose

This Proof of Concept (POC) demonstrates integrating Gitleaks, an open-source secret scanning tool, into a Jenkins CI pipeline.
The goal is to automatically scan source code for sensitive data (API keys, tokens, passwords) during the Continuous Integration (CI) process and prevent them from entering the repository

---

## 2. Pre-Requisites

- Jenkins server installed and running
- Git installed on the Jenkins agent
- Gitleaks binary installed on the Jenkins agent or master (agent recommended)
- Access to the Git repository to be scanned
- Basic understanding of Jenkins Pipeline syntax

---

## 3. System Requirements

| **Hardware/Software** | **Minimum Requirement** |
| --------------------- | ----------------------- |
| Processor             | 1 CPU (t2.micro EC2)    |
| RAM                   | 1 GiB                   |
| Disk                  | 8 GB                    |
| OS                    | Ubuntu 22.04 LTS        |
| Jenkins Version       | 2.375+                  |
| Git                   | 2.20+                   |

---

## 4. Setup and Execution

### 1. Install System Dependencies

```bash
sudo apt update
sudo apt install make
```



### 2. Install Node.js version 16

```bash
curl -fsSL https://deb.nodesource.com/setup_16.x | sudo -E bash -
sudo apt install -y nodejs
```


### 3. Check Node and npm Versions

```bash
node -v
npm -v
```

### 4. Clone the Repository

```bash
git clone https://github.com/OT-MICROSERVICES/frontend.git
cd frontend
```





### 5. Install Project Dependencies

```bash
make install
```



### 6. Build the Application

```bash
npm run build
```



- If you get “JavaScript heap out of memory”, run:
  ```bash
  NODE_OPTIONS="--max_old_space_size=4096" npm run build
  ```
  *(For low-RAM systems, use 512/1024 instead of 4096.)*

### 7. Install and Use Serve (for static hosting)

```bash
sudo npm install -g serve
serve -s build
```



### 8. Optionally, create a systemd service for auto-start

```bash
sudo nano /etc/systemd/system/frontend.service
```
_Sample Service File:_
```
[Unit]
Description=OT-MICROSERVICES Frontend ReactJS Service
After=network.target

[Service]
User=ubuntu
WorkingDirectory=/home/ubuntu/frontend
ExecStart=/usr/bin/serve -s build
Restart=on-failure

[Install]
WantedBy=multi-user.target
```

Enable and start the service:

```bash
sudo systemctl daemon-reload
sudo systemctl enable frontend.service
sudo systemctl start frontend.service
sudo systemctl status frontend.service
```





---



## 7. Troubleshooting

| Issue                        | Solution                                                         |
|------------------------------|------------------------------------------------------------------|
| JS heap out of memory        | Use `NODE_OPTIONS="--max_old_space_size=4096" npm run build`     |
| Port 3000 in use             | Run `serve -s build -l 3001` or kill previous process            |
| Cannot access externally     | Check firewall/security group for port 3000                      |
| Deprecated/vulnerable deps   | Run `npm audit fix` (optional, not blocking for deployment)      |                           |
| Compiled with warnings       | Not fatal                     |

---

## 8. Disaster Recovery & High Availability

- **Recovery:** Keep a backup of the `build/` folder and your repo.
- **HA:** Use `pm2` or a systemd service to keep `serve` running if needed.

---

## 9. FAQs

- **Is this application free?**  
  Yes, open-source.

- **Can I deploy on any cloud?**  
  Yes, on VM/container with Node.js.

- **Is there an enterprise version?**  
  No, only open-source.

---

## 10. Contact Information

| Name| Email Address      | GitHub | URL |
|-----|--------------------------|-------------|---------|
| Ishaan | ishaan.aggarwal.snaatak@mygurukulam.co|  Ishaan-Dev1  |   https://github.com/Ishaan-Dev1  |


---

## 11. References

| Description                       | Link                                                                 |
|------------------------------------|----------------------------------------------------------------------|
| Frontend API                       | https://github.com/OT-MICROSERVICES/frontend                         |
| Javascript heap out of memory      | https://geekflare.com/fix-javascript-heap-out-of-memory-error/       |
