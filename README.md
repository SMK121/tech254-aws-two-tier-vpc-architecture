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

# 🏗️ AWS Two-Tier Architecture Design

## Overview

Before implementing the AWS infrastructure, the architecture was planned to separate the application and database layers using a two-tier design.

The application server is deployed inside a **public subnet** so users can access the web application through the internet. The database server is deployed inside a **private subnet** to prevent direct public access and improve security.

The architecture uses:

- A custom VPC for network isolation
- Public subnet for the application tier
- Private subnet for the database tier
- Security Groups to control communication
- EC2 instances created from custom AMIs
- Private communication between the application and MongoDB database

The planned traffic flow is:

1. User accesses the application through the internet.
2. Traffic reaches the Application EC2 instance through the Internet Gateway.
3. Nginx forwards requests to the Node.js application.
4. The application communicates with MongoDB using the private IP address.
5. The database stores application data securely inside the private subnet.

---

## Architecture Diagram

The following diagram shows the planned AWS two-tier architecture before implementation:

![AWS Two Tier Architecture Diagram](<img width="1020" height="1447" alt="Two Tier Architecture Diagram" src="https://github.com/user-attachments/assets/51a0dfec-cdf0-446e-a315-e38e4a7964d4" />
)



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
