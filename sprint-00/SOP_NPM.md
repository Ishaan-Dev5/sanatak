# SOP: NPM(Node Package Manager)

---

### Author Information

| Author      | Created on  | Version    |   Last updated on | Internal Reviewer | L0 Reviewer  | L1 Reviewer | L2 Reviewer      |
|-------------|-------------|------------|-----------------|----------------|-------------------|---------------|----------------------------------|
| Ishaan    | 21-07-25    | v1.0  |       21-07-25       | Rohit Chopra    |  Akshit/Nitik    | Taran        | Abhishek Dubey/ Rishab sharma |

---

## Introduction
This SOP provides a standardized, step-by-step procedure to install Node Package Manager (NPM) on various operating systems..

---
## Table of Contents

1. [Introduction to NPM](#introduction-to-npm)  
2. [Prerequisites](#prerequisites)  
3. [Installation Steps](#installation-steps)  
   - [For Windows](#for-windows)  
   - [For Ubuntu / Debian-based Linux](#for-ubuntu--debian-based-linux)  
   - [For macOS using Homebrew](#for-macos-using-homebrew)  
4. [Troubleshooting](#troubleshooting)  
5. [Contact Information](#contact-information)  
6. [References](#references)

---

## Introduction to NPM
NPM (Node Package Manager) is the default package manager for Node.js.
NPM is a tool that helps manage JavaScript packages (modules/libraries). It allows developers to:
- Install, update, and remove packages (dependencies)
- Share reusable code with others
- Run scripts (e.g., build, test, start)
- Manage project dependencies via a package.json file


---

## Prerequisites

- A system with internet access to download Node.js
- Basic terminal/command line access
- Administrative/root privileges
- OS: Windows / Linux / macOS

---

## Installation Steps

### For Windows:

### 1. Download Node.js Installer:
- Visit: https://nodejs.org
- Choose LTS version for stability.
  
### 2. Run the Installer:
- Double-click the downloaded .msi file.
- Accept license agreement.
- Choose default options.
- Ensure the “npm package manager” option is selected during setup.
  
### 3. Verify Installation:
- node -v
- npm -v
  
### 4. Update NPM (optional)
To update NPM, open your terminal or command prompt and run the following command:
```
npm install -g npm@latest
```
### 5.  Start using NPM
To install a package, open your terminal or command prompt and navigate to your project directory. Then, run the following command:
```
npm install package-name
```
---

### For Ubuntu / Debian-based Linux:

### 1. Update System Packages:
```
sudo apt update && sudo apt upgrade

```
<img width="1620" height="911" alt="image" src="https://github.com/user-attachments/assets/a216f497-5476-4b61-8241-d46b6a09834d" />

### 2. Install Node.js and npm :
```
sudo apt install nodejs npm -y

```
<img width="1918" height="409" alt="image" src="https://github.com/user-attachments/assets/eacebcae-0409-4b24-a8ca-3384214bb9c8" />


### 3. Verify Installation:
```
- node -v
- npm -v
```

<img width="1179" height="226" alt="image" src="https://github.com/user-attachments/assets/ff070104-419c-493c-894d-2a9dde9c10eb" />

---

### For macOS using Homebrew:

### 1. Install Homebrew (if not already installed):



```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"


```
### 2. Install Node.js and npm :
```
brew install node

```

### 3. Verify Installation:
```
- node -v
- npm -v
```
---
## Troubleshooting

| **Issue**                           | **Resolution**                                                  |
|------------------------------------|------------------------------------------------------------------|
| `command not found: npm`           | Check if Node.js is properly installed and added to system PATH |
| npm version is outdated            | Run `npm install -g npm` to update                              |
| Permission denied errors on Linux  | Use `sudo`, or fix ownership with `chown`                       |


---
## FAQs

### 1.  Is npm installed automatically with Node.js?
Yes. When you install Node.js, npm is automatically installed as part of the package.



### 2. How do I check if npm is installed correctly?
Run the following command in your terminal or command prompt:
```
npm -v
```

### 3. How do I update npm to the latest version?
Use the command:
```
npm install -g npm@latest
```



---
## Contact Information

| Name         | Email address          |
|--------------|------------------------|
| Ishaan         | ishaan.aggarwal.snaatak@mygurukulam.co    |


---

## References

| **Title**                                 | **Link**                                                                                      |
|-------------------------------------------|-----------------------------------------------------------------------------------------------|
| Node.js official site| [Visit](https://nodejs.org/en)                    |
| npm documentation        | [Visit](https://docs.npmjs.com/about-npm)              |
| installation | [Visit](https://www.ramotion.com/blog/how-to-install-npm/)    |
 

---














