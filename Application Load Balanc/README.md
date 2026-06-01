## ALB Project

This project demonstrates the deployment of a highly available web application architecture using an AWS Application Load Balancer (ALB). The goal was to distribute incoming HTTP traffic across multiple EC2 instances while enforcing secure access controls and validating load balancing functionality.

# Project overview 

in this project, i deployed:
- Two EC2 instances inside the same VPC
- An ALB
- A target group with health checks
- Security groups with controlled traffic flow
- Web servers configured using EC2 user data scripts

The architecture ensures that all incoming traffic is handled through the ALB while preventing direct public access to the EC2 instances.


**Architectural Diagram

<img width="599" height="448" alt="IMG_7809" src="https://github.com/user-attachments/assets/1ddd3752-9daf-4f61-8ce8-63ca1b44e995" />


# EC2 instance deployment 

I launched two EC2 instances within the same VPC and placed them across different availability zones wto improve availability and fault tolerance.

**Each Instance:**
- Ran a simple web server installed through user data
- Returned different webpage content to help verify load balancing behaviour
- used a private security model with no direct public internet access

**EC2 Instance's**
<img width="1014" height="557" alt="instances-webserver" src="https://github.com/user-attachments/assets/f6035b5a-f355-47d4-880a-b05c5ef3b791" />


# Application Load Balancer Setup

I created an ALB configured across two public subnets.

The ALB configuration included:
- HTTP listener on port 80
- A target group containing both EC2 instances
- Health checks configured on the root path

The ALB was responsible for distributing incoming traffic evenly across healthy targets.

**ALB**
<img width="1021" height="427" alt="alb" src="https://github.com/user-attachments/assets/000de25d-d975-40b2-a2d9-836767630e47" />


# Target Groups

I created a Target Group and registered both EC2 instances as targets for the ALB.This ensures only healthy instances can recieve traffic.

**Target group**

<img width="1018" height="400" alt="targets healthy" src="https://github.com/user-attachments/assets/557a808f-2662-4c2e-b1db-3eab18435659" />




# Security Groups 

Security groups were configured to enforce secure communication between components.

**ALB Security Group**
- Allowed HTTP from anywhere

**EC2 Security Group**
- Allowed HTTP only from the ALB SG
- No direct public access allowed

This ensured that all external traffic flowed through the ALB rather than directly to servers.














