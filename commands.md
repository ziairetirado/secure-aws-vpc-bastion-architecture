# SSH Commands Used

## Laptop → Bastion
# Bastion → Private EC2
# bash
ssh -i *.pem ec2-user@<BASTION_PUBLIC_IP>

ssh -i *.pem ec2-user@<PRIVATE_EC2_PRIVATE_IP>
# Key Permissions
chmod 400 *.pem
# SCP Key to Bastion
scp -i *.pem *.pem ec2-user@<BASTION_PUBLIC_IP>:~/

# Step 3: Push to GitHub
# bash
git init
git add .
git commit -m "Initial commit: Secure AWS VPC with bastion host"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/aws-bastion-private-ec2.git
git push -u origin main
