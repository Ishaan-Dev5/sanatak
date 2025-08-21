
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

---


## 3. System Requirements

---

## 4.Setup and execution

### Before starting dependency test, ensure that you have Maven installed on your system. 

####  Step 1. Clone the repo from github

```
sudo git clone https://github.com/OT-MICROSERVICES/salary-api.git
```

<img width="600" height="187" alt="image" src="https://github.com/user-attachments/assets/b7270856-908e-4309-9bee-42955c6c8144" />


#### Step 2. Change the repo choose the github repo which is cloned already

```
cd salary-api
```

<img width="600" height="81" alt="image" src="https://github.com/user-attachments/assets/92cd41a7-4e8a-41f2-8dbb-619bd94bd199" />


####  Step 3. Dependency checking
```
mvn org.owasp:dependency-check-maven:check
```



#### Step 4. View the Dependency Result 

```
google-chrome target/site/index.html

```

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
