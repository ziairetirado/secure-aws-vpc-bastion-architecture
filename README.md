# Secure AWS VPC with Bastion Host and Private EC2

This project demonstrates a secure, enterprise-style AWS network architecture using a **custom VPC**, **segmented subnets**, a **bastion host**, and a **private EC2 instance** that is accessible only through controlled SSH hopping.

All identifiers, IP addresses, and account-specific details have been intentionally sanitized for security purposes.

---

## Architecture Overview

- Custom VPC (sanitized name)
- Public subnet hosting a Bastion Host
- Private subnet hosting an application EC2 instance
- No direct public internet access to the private EC2
- SSH access enforced exclusively through the Bastion Host

---

## Components

- **VPC**  
  Custom VPC with a private RFC1918 CIDR range (example: `10.0.0.0/16`)

- **Public Subnet**  
  Hosts the Bastion EC2 instance with controlled public access

- **Private Subnet**  
  Hosts a private EC2 instance with no public IP assigned

- **Security Groups**  
  - Bastion security group allows SSH only from a trusted source  
  - Private EC2 security group allows SSH **only** from the Bastion security group

- **Access Method**  
  Multi-hop SSH access pattern:
  - Laptop → Bastion Host → Private EC2

---

## SSH Flow

```text
Client Machine
     ↓ SSH
Bastion Host (Public Subnet)
     ↓ SSH
Private EC2 (Private Subnet)
