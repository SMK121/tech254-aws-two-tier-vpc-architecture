# 🚀 AWS Two-Tier Architecture Deployment with VPC, EC2 and MongoDB

## 📌 Project Overview

This project demonstrates the design and deployment of a secure two-tier architecture on AWS.

The architecture separates the application and database layers by placing:

- Application server in a public subnet
- Database server in a private subnet

The deployment uses:

- AWS VPC
- Public and private subnets
- Internet Gateway
- Route Tables
- Security Groups
- EC2 instances
- Custom AMIs
- Node.js application
- MongoDB database
- Nginx reverse proxy
- PM2 process management


---

# 🏗️ Planned Architecture Diagram

(Add architecture diagram here)

![AWS Two Tier Architecture](./diagrams/aws-two-tier-diagram.png)


---

# 📋 Implementation Plan

## Step 1 - Create VPC

Create a dedicated VPC to isolate AWS resources.

Configuration:

- VPC CIDR: `10.0.0.0/16`

Screenshot:

(Add VPC screenshot here)

![VPC Creation](./screenshots/vpc.png)


---

# Step 2 - Create Public and Private Subnets

## Public Application Subnet

Purpose:

- Hosts application EC2 instance
- Allows external user access

Configuration:

- CIDR: `10.0.2.0/24`

Screenshot:

(Add public subnet screenshot)

![Public Subnet](./screenshots/public-subnet.png)


---

## Private Database Subnet

Purpose:

- Hosts MongoDB database
- Prevents direct internet access

Configuration:

- CIDR: `10.0.3.0/24`

Screenshot:

(Add private subnet screenshot)

![Private Subnet](./screenshots/private-subnet.png)


---

# Step 3 - Configure Routing

## Internet Gateway

Allows public subnet resources to communicate with the internet.

Screenshot:

(Add Internet Gateway screenshot)


## Route Tables

Public route:
