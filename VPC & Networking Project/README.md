# Custom VPC & Networking Project 

## Overview
This project demonstrates the creation of a fully custom AWS networking environment from scratch. The goal was to build a secure and segmented cloud network architecture with both public and private subnets, congifured routing, controlled internet access and EC2 deployment across isolated environments.


## Architecture
- Custom VPC (10.0.0.0/16)
- Public Subnet
- Private Subnet
- Internet Gateway (IGW)
- NAT Gateway
- Security groups
- Public EC2 instance
- Private EC2 instance

## Architecture Diagram
<img width="632" height="421" alt="IMG_7806" src="https://github.com/user-attachments/assets/5d94f66f-2029-47f6-9c80-18dde9f147d1" />


## Key Features

# Custom Networking 
Started by creating a custom VPC using the CIDR block 10.0.0.0/16.This provided a private network space where all the resources for the project would exist.



<img width="997" height="496" alt="asm1 vpc" src="https://github.com/user-attachments/assets/0f333ddc-a49c-405d-b620-8defb6b7bd64" />




After creating the VPC, i configured:
- public subnet
- private subnet 

The public subnet was designed for resources requiring direct internet access, while the private subnet was intended for internal-only resources.


# Configuring internet access

To allow external connectivity, i attached an internet gateway (IGW) to the VPC.

Allocated an Elastic IP, Created a NAT gateway inside the public subnet , Associated the Elastic IP with the NAT gateway.

The NAT gateway allowed resources inside the private subnet to access the internet for updates,package installations, etc, without exposing them directly to inbound traffic.

# Route tables

AWS automatically handles route tables during the creation of a VPC. I reviewed the routing configuration to ensure :

- The public subnet route table included a default route to the IGW
- The private subnet route inclided a default route to the NAT Gateway

<img width="988" height="517" alt="safe public route" src="https://github.com/user-attachments/assets/0757f288-735c-4a5c-b271-d13a6d9660be" />

<img width="996" height="504" alt="safe private route" src="https://github.com/user-attachments/assets/1b1fe849-84c0-4af7-adae-c15d8bd5ec59" />






# Resource Map
<img width="997" height="514" alt="safe resource map" src="https://github.com/user-attachments/assets/8d055006-9a73-4873-a8a1-39253c5798c9" />


# Security Groups

Security Groups were configured before launching EC2 instances.

**Public EC2 Security Group**
- Allow SSH access only from my IP address
- Allow HTTP access only from my IP address

**Private EC2 Security Group**
- Allow only internal access / from public EC2


# Launching EC2 Instances

**Public EC2 Instance**
- Deployed in the public Subnet
- Assigned a public IPv4 address
- Associated with public security group

**Private EC2 Instance**
- Launched in private Subnet
- No public IPv4 assigned
- Fully isolated from direct internet access
- Accessible only within the VPC via the public EC2 (Bastion host)
- Associated with private security group

<img width="795" height="235" alt="asm1-instances" src="https://github.com/user-attachments/assets/93f1d71f-d394-4dc2-bc4b-35234b892672" />

# Testing & Validation

To validate the VPC setup, I tested connectivity between resources:
- Successfully established an SSH connection from my local machine to the public EC2 instance.
- From the public EC2 instance (acting as a bastion host), I SSH'd into the private EC2 instance using its private IP address.

**This confirmed**
- Public subnet is accessible from the internet
- Private subnet is isolated from direct external access
- Internal VPC communication between subnets is functioning properly

**Pub EC2 SSH**
<img width="444" height="212" alt="asm1 PubEC2 testing" src="https://github.com/user-attachments/assets/a176f02b-38bc-4720-ab81-164bb5706a33" />

**Priv EC2 SSH**
<img width="445" height="261" alt="real privec2 screenshot" src="https://github.com/user-attachments/assets/b1ffa897-f5c7-4060-a6bd-e7518caa0a93" />



















