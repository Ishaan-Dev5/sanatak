# SOP: NPM(Node Package Manager)

---

| Author      | Created on  | Version    | Last updated by | Last edited on |
|-------------|-------------|------------|-----------------|----------------|
| Ishaan    | 21-07-25    | version 1  | Ishaan        | 21-07-25       |

## Introduction
This SOP provides a standardized, step-by-step procedure to install Node Package Manager (NPM) on various operating systems..


## Table of Contents

1. [Introduction to NPM](#introduction=to-npm)
2. [ What does NPM stand for and why is it important?](#What-does-NPM-stand-for-and-why-is-it-important?)
3. [Prerequisites](#Prerequisites)  
4. [Installation Steps](#Installation-Steps)
      - [For Windows](#For-Windows:)
      - [For Ubuntu / Debian-based Linux](#For-Ubuntu-/-Debian-based-Linux:)
      - [For macOS(using Homebrew)](#For-macOS(using-Homebrew):)
5. [Troubleshooting](#troubleshooting)
6. [Contact Information](#contact-information)
7. [References](#references)


## Introduction to NPM
**To explore benefits of playbook**: [Playbook Introduction](https://github.com/snaatak-Downtime-Crew/Documentation/blob/adil_scrums_48/common_stack/ansible/playbook/intro/README.md#2-why-ansible-playbook)

## What does NPM stand for and why is it important?
**To get an overview of playbook**: [Playbook Introduction](https://github.com/snaatak-Downtime-Crew/Documentation/blob/adil_scrums_48/common_stack/ansible/playbook/intro/README.md#3-what-is-ansible-playbook)

## Prerequisites

- A system with internet access
- Basic terminal/command line access
- Administrative/root privileges
- OS: Windows / Linux / macOS

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

### For Ubuntu / Debian-based Linux:

### 1. Update System Packages:
```
sudo apt update && sudo apt upgrade

```
### 2. Install Node.js and npm :
```
sudo apt install nodejs npm -y

```

### 3. Verify Installation:
```
- node -v
- npm -v
```

### For macOS(using Homebrew):

### 1. nstall Homebrew (if not already installed):



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
## Troubleshooting

| **Issue**                           | **Resolution**                                                  |
|------------------------------------|------------------------------------------------------------------|
| `command not found: npm`           | Check if Node.js is properly installed and added to system PATH |
| npm version is outdated            | Run `npm install -g npm` to update                              |
| Permission denied errors on Linux  | Use `sudo`, or fix ownership with `chown`                       |



## Contact Information

| Name         | Email address          |
|--------------|------------------------|
| Ishaan         | ishaan.aggarwal.snaatak@mygurukulam.co    |




## References

| **Title**                                 | **Link**                                                                                      |
|-------------------------------------------|-----------------------------------------------------------------------------------------------|
| Node.js official site| [Visit](https://nodejs.org/en)                    |
| npm documentation        | [Visit](https://docs.npmjs.com/about-npm)              |


---














