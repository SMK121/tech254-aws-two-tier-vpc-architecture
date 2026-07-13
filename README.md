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

# 🏗️ AWS Two-Tier Architecture Diagram

```mermaid

flowchart TD

    User[User / Browser]

    Internet[Internet]

    IGW[Internet Gateway]

    subgraph VPC[tech610-suhaib-2tier-first-vpc]

        subgraph Public[Public Subnet - 10.0.2.0/24]

            App[Application EC2 VM<br/>
            Node.js + PM2 + Nginx<br/>
            Private IP: 10.0.2.124<br/>
            Public IP: 54.74.79.228]

        end

        subgraph Private[Private Subnet - 10.0.3.0/24]

            DB[Database EC2 VM<br/>
            MongoDB<br/>
            Private IP: 10.0.3.93]

        end

    end

    User --> Internet
    Internet --> IGW
    IGW --> App

    App -->|MongoDB Port 27017| DB
```



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
