# Secure AWS VPC with Bastion Host and Private EC2

This project demonstrates a secure, enterprise-style AWS network architecture using a custom VPC, public and private subnets, a bastion host, and a private EC2 instance accessible only through SSH hopping.

## 🔐 Architecture Overview

- Custom VPC (`lab-vpc`)
- Public subnet for Bastion Host
- Private subnet for application EC2
- No public internet access to private EC2
- SSH access enforced through Bastion Host only

## 🧱 Components

- **VPC**: Custom VPC with CIDR block (example: 10.0.0.0/16)
- **Public Subnet**: Hosts Bastion EC2 with public IP
- **Private Subnet**: Hosts private EC2 with no public IP
- **Security Groups**:
  - Bastion SG allows SSH from trusted IP
  - Private EC2 SG allows SSH only from Bastion SG
- **Access Method**: SSH hop (Laptop → Bastion → Private EC2)

## 🔁 SSH Flow

```text
Laptop
  ↓ SSH
Bastion Host (Public Subnet)
  ↓ SSH
Private EC2 (Private Subnet)
