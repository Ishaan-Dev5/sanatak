# POC of OT-MICROSERVICES Frontend

---

## Author Information

| **Author**   | **Created on** | **Version** | **Last updated by** | **Last edited on** | **Level** | **Reviewer**  |
|--------------|----------------|-------------|---------------------|--------------------|-----------|---------------|
| Ishaan       | 30-07-25       | v1.0        | Ishaan              | 30-07-25           | Internal  | Rohit Chopra  | 

---

## Table of Contents

1. [Purpose](#1-purpose)  
2. [Pre-Requisites](#2-pre-requisites)  
3. [System Requirements](#3-system-requirements)   
4. [Ports](#4-ports)  
5. [Setup and Execution](#5-setup-and-execution)  
6. [Monitoring and Logging](#6-monitoring-and-logging)  
7. [Troubleshooting](#7-troubleshooting)  
8. [Disaster Recovery & High Availability](#8-disaster-recovery--high-availability)  
9. [FAQs](#9-faqs)  
10. [Contact Information](#10-contact-information)  
11. [References](#11-references)  

---

## 1. Purpose

The OT-MICROSERVICES Frontend is a ReactJS web application that provides the main user interface for the OT-Microservices stack. It enables management and visualization of employee, attendance, and salary information by communicating with the backend REST APIs.

---

## 2. Pre-Requisites

- Node.js (v12.22.9 or later recommended)
- npm (v8.5.1 or later)
- GNU Make (v4.3 or later)
- Access/configuration for the following backend REST APIs:
  - Employee API
  - Attendance API
  - Salary API

---

## 3. System Requirements

| Hardware/Software | Minimum Recommendation  |
|-------------------|------------------------|
| Processor         | 1 CPU (t2.micro EC2)   |
| RAM               | 1 GiB                  |
| Disk              | 8 GB                   |
| OS                | Ubuntu 22.04 LTS       |

---

## 4. Ports

| Port | Service              | Description                         |
|------|---------------------|-------------------------------------|
| 22   | SSH                 | Remote terminal access              |
| 3000 | HTTP (ReactJS)      | Default frontend port               |

---

## 5. Setup and Execution

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

### 3. Clone the Repository

```bash
git clone https://github.com/OT-MICROSERVICES/frontend.git
cd frontend
```

### 4. Check Node and npm Versions

```bash
node -v
npm -v
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

## 6. Monitoring and Logging

- **Process Monitoring:** Use `htop`, `top` for CPU/RAM.
- **Logs:** Terminal output of `serve`/`npm start`. For errors, check the browser console.
- **Health:** If the page loads, the app is healthy.

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
| Create React App Deployment Docs   | https://bit.ly/CRA-deploy                                            |


