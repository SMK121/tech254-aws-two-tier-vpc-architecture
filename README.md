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


VPC:
tech610-suhaib-2tier-first-vpc

CIDR:
10.0.0.0/16


The VPC contains two subnets:

| Subnet | Purpose | CIDR |
|-|-|-|
| Public Subnet | Application EC2 instance | 10.0.2.0/24 |
| Private Subnet | MongoDB Database EC2 instance | 10.0.3.0/24 |

The application is placed in the public subnet so users can access it, while the database remains private for security.



## VPC Resource Map

The AWS VPC Resource Map provides a visual overview of the network design.

It shows the relationship between:

- The custom VPC
- Public and private subnets
- Route tables
- Internet Gateway connection

This confirms the application and database layers were separated correctly within the VPC before deploying the EC2 instances.

![VPC Resource Map](https://github.com/user-attachments/assets/796c47f1-e0ed-48d7-8b3d-f2ed2abb4498)




# 🔒 Security Groups

# 🔒 Security Groups

Security Groups were created to control traffic between the application and database tiers.

## Application Security Group

The application server uses a Security Group to allow web traffic from users and secure administrative access.

Inbound rules:

| Type | Port | Source | Purpose |
|-|-|-|-|
| HTTP | 80 | 0.0.0.0/0 | Allows users to access the web application |
| SSH | 22 | My IP (2.102.169.57/32) | Allows secure administration access |



### Screenshot

![Application Security Group](https://github.com/user-attachments/assets/b7904eb8-57b1-4b40-942b-d6fcec88a000)



### Database Security Group

Allows:

- MongoDB (Port 27017) communication only from the application subnet
- SSH (Port 22) for administration


---

# 🖥️ EC2 Deployment

Custom AMIs were used to deploy both servers.


## Application Server

Deployed using:


AMI:
tech610-Suhaib-ready-to-run-ttt-app-image


Configuration:


Subnet:
tech610-suhaib-public-subnet

Private IP:
10.0.2.124

Public IP:
54.74.79.228


Runs:

- Nginx
- Node.js application
- PM2

---

## Database Server

Deployed using:


AMI:
tech610-Suhaib-ready-to-run-ttt-db-image


Configuration:


Subnet:
tech610-suhaib-private-subnet

Private IP:
10.0.3.93


Runs:

- MongoDB database

---


# ✅ Final Application Verification

The completed deployment was tested by accessing the application through the Application EC2 public IP.

Verified:

✅ Application loads successfully  
✅ Application connects to MongoDB  
✅ Data is persisted using the database server  
✅ Two-tier architecture is working correctly  


### Final Application Screenshot

![Working Tic Tac Toe Application](https://github.com/user-attachments/assets/bcdf8172-9e7c-4c02-bd38-6921ff7725fc)




