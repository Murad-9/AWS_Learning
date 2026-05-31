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

After creating the VPC, i configured:
- public subnet
- private subnet 

The public subnet was designed for resources requiring direct internet access, while the private subnet was intended for internal-only resources.


# Configuring internet access

To allow external connectivity, i attatched an internet gateway (IGW) to the VPC.

Allocated an Elastic IP, Created a NAT gateway inside the public subnet , Associated the Elastic IP with the NAT gateway.

The NAT gateway allowed resources inside the private subnet to access the internet for updates,package installations, etc, without exposing the, directly to inbound traffic.

# Resource Map
<img width="997" height="514" alt="safe resource map" src="https://github.com/user-attachments/assets/8d055006-9a73-4873-a8a1-39253c5798c9" />







