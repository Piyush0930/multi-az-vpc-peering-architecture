# AWS VPC Peering (Multi-AZ) - POC 

##  Overview

This project demonstrates a **VPC Peering setup in AWS** to enable **private communication between two VPCs** across multiple Availability Zones.

---

##  Objective

* Understand VPC as a regional service
* Implement **Multi-AZ architecture**
* Establish **secure private connectivity** between VPCs
* Transfer data using private IP (no internet)

---

##  Architecture

Region: ap-south-1 (Mumbai)

VPC-1 (10.0.0.0/16)

* Subnet-A (10.0.1.0/24) → EC2-1
* Subnet-B (10.0.2.0/24)

VPC-2 (10.1.0.0/16)

* Subnet-A (10.1.1.0/24) → EC2-2
* Subnet-B (10.1.2.0/24)

VPC Peering Connection established between both VPCs

---

## ⚙️ Services Used

* Amazon VPC
* Amazon EC2
* Internet Gateway
* Route Tables
* Security Groups

---

## 🔧 Implementation Steps

### 1. Create VPCs

* VPC-1 → 10.0.0.0/16
* VPC-2 → 10.1.0.0/16

### 2. Create Subnets (Multi-AZ)

* Each VPC has 2 subnets across different AZs

### 3. Launch EC2 Instances

* One EC2 in each VPC

### 4. Configure Internet Gateway

* Attached to both VPCs for SSH access

### 5. Create VPC Peering Connection

* Request from VPC-1 → Accept in VPC-2

### 6. Update Route Tables

* VPC-1 → Route to 10.1.0.0/16
* VPC-2 → Route to 10.0.0.0/16

### 7. Configure Security Groups

* Allow SSH (22)
* Allow ICMP (Ping)

---

## 🔁 Testing

### Connectivity Test

Ping EC2-2 from EC2-1 using private IP:

```
ping <EC2-2-PRIVATE-IP>
```

### File Transfer Test

Transfer file using SCP:

```
scp file.txt ec2-user@<EC2-2-PRIVATE-IP>:/home/ec2-user/
```

---

## ✅ Results

* Successful private communication between VPCs
* Multi-AZ architecture validated
* File transfer completed using private IP

---

## 🔐 Key Learnings

* VPC is a regional service
* Subnets are AZ-specific
* VPC Peering enables private networking
* Route tables and security groups are critical

---

## 🚀 Future Enhancements

* Cross-region VPC peering
* Transit Gateway implementation
* Terraform automation
* Multi-account architecture

---

## 👨‍💻 Author

Piyush Patil

---
