# SSH Commands Used

This file demonstrates SSH commands and Git workflow for the private EC2 / bastion host setup. **All sensitive information such as keys and IP addresses has been sanitized.**

## SSH Access

### Laptop → Bastion Host
# bash
ssh -i <YOUR_KEY.pem> ec2-user@<BASTION_PUBLIC_IP>

### Bastion Host → Private EC2
ssh -i <YOUR_KEY.pem> ec2-user@<PRIVATE_EC2_PRIVATE_IP>

### Key Permissions
chmod 400 <YOUR_KEY.pem>

### Copy Key to Bastion
# If using bastion as an intermediate hop:
scp -i <YOUR_KEY.pem> <YOUR_KEY.pem> ec2-user@<BASTION_PUBLIC_IP>:~/

### GitHub Workflow (Publishing Repo)
git init
git add .
git commit -m "Initial commit: Secure AWS VPC with bastion host"
git branch -M main
git remote add origin https://github.com/<YOUR_USERNAME>/<REPO_NAME>.git
git push -u origin main


### Notes on Security
- All `.pem` filenames replaced with `<YOUR_KEY.pem>` placeholder  
- All IP addresses replaced with `<BASTION_PUBLIC_IP>` and `<PRIVATE_EC2_PRIVATE_IP>`  
- GitHub push workflow generalized  
