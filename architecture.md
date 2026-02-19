#  architecture.md (TECHNICAL BREAKDOWN)

```md
# Architecture Details

## VPC
- Name: lab-vpc
- CIDR: 10.0.x.x <PRIVATE_EC2_PRIVATE_IP>

## Subnets
### Public Subnet
- Hosts Bastion EC2
- Route to Internet Gateway

### Private Subnet
- Hosts Private EC2
- No public IP assigned

## Bastion Host
- Amazon Linux 2023
- Public IPv4 enabled
- SSH allowed from trusted IP only

## Private EC2
- Amazon Linux 2023
- No public IPv4
- SSH allowed only from Bastion Security Group

## Security Model
- No inbound internet access to private EC2
- Bastion acts as controlled access point
