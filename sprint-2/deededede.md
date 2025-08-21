
<img width="400" height="376" alt="image" src="https://github.com/user-attachments/assets/adae343f-32b7-44e2-81f3-b8da98af9784" />


#  POC of Dependency Scanning in Java CI Checks

##   Author Information

| **Author**   | **Created on** | **Version** | **Last updated by** | **Last edited on** | **Level** | **Reviewer**  |
|--------------|----------------|-------------|---------------------|--------------------|-----------|---------------|
| Tina Bhatnagar  | 17-08-25    | v1.0  |  Tina Bhatnagar |17-08-25     | Internal    | Rohit Chopra    |



# Table of Contents  

1. [Introduction](#1-introduction)
2. [Prerequisites](#2-Prerequisites)
3. [System Requirements](#3-System-Requirements)
4. [Setup and execution](#4-setup-instructions)  
5. [Conclusion](#5-conclusion)
6. [Troubleshooting](#6-Troubleshooting) 
7. [Contact information](#7-Contact-information)  
8. [References](#8-references)  


## 1. Introduction


---

## 2. Prerequisites

- **Java**: Java 17 (JDK/JRE)   
- **Internet Access**: To update CVE database (NVD, NPM, etc.)   
- **Build Tool**: Maven/Gradle 
- **NVD API Key (optional but recommended)**: To updates NVD databases fast  
---


## 3. System Requirements


| Requirement        | Minimum                | Recommended                       |
|--------------------|------------------------|-----------------------------------|
| CPU                | 1 vCPU                | 2+ vCPU                           |
| RAM                | 2 GB                  | 4+ GB                             |
| Disk Space         | 2 GB (for CVE DB cache) | 5+ GB (large CVE database + reports) |



---

## 4.Setup and execution

```bash

sudo apt update
sudo apt install openjdk-17-jdk -y
java -version
```

```bash
wget https://github.com/jeremylong/DependencyCheck/releases/download/v12.1.0/dependency-check-12.1.0-release.zip
 unzip dependency-check-12.1.0-release.zip
cd dependency-check
```

```bash
./bin/dependency-check.sh --updateonly
```


```bash
sudo apt install maven -y
```

```bash
mvn clean package -DskipTests
```

```bash
 dependency-check.sh --project salary --scan /home/ubuntu/salary-api/target --format HTML --out /home/ubuntu/dc-report.html
```

```bash
 python3 -m http.server 8080
```

http://13.203.25.45:8080/dc-report.html


---

## 5. Conclusion

---

## 6. Troubleshooting

---


## 7. Contact information


| Name| Email Address      | GitHub | URL |
|-----|--------------------------|-------------|---------|
| Tina Bhatnagar | [tina.bhatnagar@mygurukulam.co](mailto:tina.bhatnagar@mygurukulam.co)|  tina-snatak  | https://github.com/tina-snatak/ |

---

## 8. References

| **Title** | **Link** |
|-----------|----------|
| Dependancy Scanning |[Link](https://docs.gitlab.com/ee/user/application_security/dependency_scanning/) 
| Dependancy Scanning tool |[Link](https://finitestate.io/blog/best-java-scanner)
