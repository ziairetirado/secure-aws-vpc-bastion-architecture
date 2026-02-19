# Architecture Details

## VPC
- Name: Custom VPC (sanitized)
- CIDR: Private RFC1918 range (example: 10.0.x.x)

## Subnets
### Public Subnet
- Hosts Bastion EC2
- Routed to Internet Gateway for controlled access

### Private Subnet
- Hosts Private EC2
- No public IP assigned
- Isolated from direct internet access

## Bastion Host
- Amazon Linux 2023
- Public IPv4 enabled (sanitized)
- SSH access allowed only from trusted client IP(s)
- Serves as controlled entry point to private subnet

## Private EC2
- Amazon Linux 2023
- No public IPv4
- SSH access allowed only from Bastion security group
- Fully isolated from external internet

## Security Model
- Multi-layer access control: Bastion host enforces SSH hop
- Private EC2 inaccessible directly from the internet
- Security groups enforce least-privilege network trust
- Architecture mirrors real-world enterprise AWS environments

