<img width="400" height="101" alt="Terraform Drift" src="https://github.com/user-attachments/assets/cce9c229-5b1b-45ed-81d7-b7ef3db1b474" />

# Drift POC

---

## Author Information

| **Author**   | **Created on** | **Version** | **Last updated by** | **Last edited on** | **Level** | **Reviewer**  |
|--------------|----------------|-------------|---------------------|--------------------|-----------|---------------|
| Ishaan       | 16-09-25       | v1.0        | Ishaan              | 16-09-25           | Internal  | Rohit Chopra  | 

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

This Proof of Concept (POC) demonstrates integrating Terraform’s drift detection.

---

## 2. Pre-Requisites

- Terraform
- Cloud provider CLI installed and configured 


---

## 3. System Requirements

| **Hardware/Software** | **Minimum Requirement** |
| --------------------- | ----------------------- |
| Processor             | 1 CPU (t2.micro EC2)    |
| RAM                   | 1 GiB                   |
| Disk                  | 8 GB                    |
| OS                    | Ubuntu 22.04 LTS        |


---

## 4. Setup and Execution

### 1. Create terraform files to create a AWS resource

#### main.tf
```hcl
provider "aws" {
  region = "ap-south-1"
}

resource "aws_s3_bucket" "demo_bucket" {
  bucket = "terraform-drift-demo-unique-12345"


  tags = {
    Name        = "TerraformDriftDemoBucket"
    Environment = "POC"
  }
}
```
#### outputs.tf

```hcl
output "bucket_name" {
  value = aws_s3_bucket.demo_bucket.id
}
```

---

### 2. Run terraform commands

```hcl
    terraform init
```
<img width="1919" height="429" alt="image" src="https://github.com/user-attachments/assets/be3f0004-7272-4426-9aa6-699c8ccb8756" />

```hcl
    terraform plan
```
<img width="1919" height="952" alt="image" src="https://github.com/user-attachments/assets/ef22012d-91b7-437a-9e9c-3ccfcf6ec091" />

```hcl
   terraform apply -auto-approve
```
<img width="1913" height="939" alt="image" src="https://github.com/user-attachments/assets/7ef5211c-9857-4a2f-829f-017806669ef6" />

---

### 3. Verify your resources on AWS

<img width="1919" height="929" alt="image" src="https://github.com/user-attachments/assets/c670af34-5e98-4a97-971e-335e840124ba" />

---

### 4. Change tag on the resource using AWS console

<img width="1919" height="856" alt="image" src="https://github.com/user-attachments/assets/988060ef-9f97-4338-bb53-b6d57ce6f757" />

---


### 5.  For Drift detection

#### run terraform plan
```hcl
 terraform plan
```

#### drift detected

<img width="1918" height="677" alt="image" src="https://github.com/user-attachments/assets/651f6cf0-774d-484e-a25c-b08e764322fe" />

---



### 6. To fix the drift

```hcl
terraform apply -auto-approve
```
<img width="1919" height="839" alt="image" src="https://github.com/user-attachments/assets/6bc1809f-c3de-4b14-a05e-c372e0594899" />

---








## 5. Troubleshooting

| **Issue**                                          | **Solution**                                                                                 |
| -------------------------------------------------- | -------------------------------------------------------------------------------------------- |
| `BucketAlreadyExists` or `BucketAlreadyOwnedByYou` | Change the S3 bucket name to a globally unique one in `main.tf`.                             |
| `InsufficientPermissions`                          | Ensure AWS IAM user has proper permissions (`s3:CreateBucket`, `s3:PutBucketTagging`, etc.). |
| Terraform plan shows unexpected changes            | Review drift in `terraform plan` and apply fixes with `terraform apply -auto-approve`.       |
| Drift not detected                                 | Run `terraform plan -detailed-exitcode` after making manual changes to the infrastructure.   |

---

## 6. Best Practices

- Avoid manual changes in the cloud; update Terraform code instead.
- Keep Terraform CLI and provider versions up-to-date to avoid deprecation issues.
- Use remote state storage with locking (e.g., S3 + DynamoDB for AWS).
- Tag resources consistently to track and manage infrastructure easily.

---




## 7. FAQs

#### 1. **What is drift in Terraform?**
Drift occurs when the actual infrastructure in the cloud differs from what is defined in Terraform code.

#### 2. **How can I detect drift?**
Run terraform plan -detailed-exitcode

#### 3. **Does running terraform refresh detect drift?**
No. terraform refresh updates the state file to match the actual infrastructure, which will hide any drift. Use terraform plan without refresh to detect drift.

---

## 8. Contact Information

| Name| Email Address      | GitHub | URL |
|-----|--------------------------|-------------|---------|
| Ishaan | ishaan.aggarwal.snaatak@mygurukulam.co|  Ishaan-Dev1  |   https://github.com/Ishaan-Dev1  |


---

## 9. References

| Description                       | Link                                                                 |
|------------------------------------|----------------------------------------------------------------------|
| Terraform Drift Document                       | [Link]()                         |

