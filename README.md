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

![AWS Two Tier Architecture Diagram](https://github.com/user-attachments/assets/51a0dfec-cdf0-446e-a315-e38e4a7964d4)


# 🌐 VPC and Subnet Setup

A custom VPC was created to provide an isolated AWS network for the two-tier architecture.

The VPC contains two subnets:

- **Public Subnet** - Hosts the application EC2 instance and allows internet access through the Internet Gateway.
- **Private Subnet** - Hosts the MongoDB database EC2 instance and restricts direct internet access.

Configuration:





