# POC of OT-MICROSERVICES Frontend

---

## Author Information

| **Author**   | **Created on** | **Version** | **Last updated by** | **Last edited on** | **Level** | **Reviewer**  |
|--------------|----------------|-------------|---------------------|--------------------|-----------|---------------|
| Ishaan       | 1-08-25       | v1.0        | Ishaan              | 1-08-25           | Internal  | Rohit Chopra  | 

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
<img width="1919" height="804" alt="Screenshot 2025-08-01 000718" src="https://github.com/user-attachments/assets/201c9c86-d53b-4e0e-831a-269872ae93ba" />


### 2. Install Node.js version 16

```bash
curl -fsSL https://deb.nodesource.com/setup_16.x | sudo -E bash -
sudo apt install -y nodejs
```
<img width="1919" height="876" alt="Screenshot 2025-08-01 001030" src="https://github.com/user-attachments/assets/ca73869e-d45a-4f49-8efe-017d3498dab8" />

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
<img width="1919" height="362" alt="Screenshot 2025-08-01 000853" src="https://github.com/user-attachments/assets/d96ff094-1a6a-4428-beaf-c9653df2ea6e" />




### 5. Install Project Dependencies

```bash
make install
```
<img width="1919" height="913" alt="Screenshot 2025-08-01 001232" src="https://github.com/user-attachments/assets/efb0b5a0-0334-438d-9367-5b0c0133475f" />


### 6. Build the Application

```bash
npm run build
```

<img width="1297" height="198" alt="Screenshot 2025-08-01 001520" src="https://github.com/user-attachments/assets/a1255a34-b709-4968-93c2-d26813b741ea" />

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
<img width="1293" height="441" alt="Screenshot 2025-08-01 001622" src="https://github.com/user-attachments/assets/128c2675-850a-455e-ac87-e7a385435450" />

<img width="1919" height="868" alt="Screenshot 2025-08-01 001711" src="https://github.com/user-attachments/assets/9adc145e-c8b9-495a-bdb1-354e85b21b94" />


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
<img width="1651" height="546" alt="Screenshot 2025-08-01 002032" src="https://github.com/user-attachments/assets/1b961ae3-a922-4493-93c7-0eac2f53a1d4" />


<img width="1919" height="869" alt="Screenshot 2025-08-01 001721" src="https://github.com/user-attachments/assets/dc0008a9-0745-4f85-855c-76869d7396db" />



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

