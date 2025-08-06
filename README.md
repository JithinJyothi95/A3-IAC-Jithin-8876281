
# Assignment 3: Deploying AWS Infrastructure with CloudFormation

---

## Project Overview

This project demonstrates the provisioning of AWS infrastructure using AWS CloudFormation through three separate stacks:

- **Networking Stack**: VPC, subnets, and internet gateway setup
- **RDS Stack**: MySQL RDS instance with security groups and subnet groups
- **EC2 Stack**: Amazon EC2 instance configured in the public subnet

Each component was deployed using a separate YAML template and verified via the AWS Console and CLI.

---

## Folder Structure

```
A3-IAC-JITHIN-8876281/
├── screenshots/                # Contains proof of stack creation and instance visibility
├── templates/                  # CloudFormation YAML templates for each stack
│   ├── ec2.yaml
│   ├── network.yaml
│   └── rds.yaml
├── a3-keypair-jithin.pem       # EC2 SSH key (not uploaded to GitHub)
├── .gitignore                  # To prevent committing sensitive files
├── README.md                   # Assignment summary
```

---

## Deployed Resources

### 1. Networking Stack (`network.yaml`)

- **Stack Name**: `jithin-networking-stack`
- **Resources**: VPC, public/private subnets, route table, internet gateway, outputs
- **Command**:
```bash
aws cloudformation create-stack   --stack-name jithin-networking-stack   --template-body file://templates/network.yaml   --capabilities CAPABILITY_NAMED_IAM
```

**Screenshots**:

![Network Stack Created](screenshots/network%20creation%20success.png)  
![VPC and Subnets via CLI](screenshots/network-ec2-CLI.png)  
![VPC](screenshots/vpc.png)  
![Subnets](screenshots/subnets.png)  
![Internet Gateway](screenshots/Internet-gateway.png)  
![Stack Output](screenshots/network-output-stack.png)

---

### 2. RDS Stack (`rds.yaml`)

- **Stack Name**: `jithin-rds-stack`
- **Resources**: Security Group for MySQL, RDS Instance in private subnet
- **Command**:
```bash
aws cloudformation create-stack   --stack-name jithin-rds-stack   --template-body file://templates/rds.yaml   --capabilities CAPABILITY_NAMED_IAM
```

**Screenshots**:

![RDS Stack Created](screenshots/rds%20creation%20success.png)  
![RDS CLI Confirmation](screenshots/RDS%20CLI.png)  
![Running RDS Instance](screenshots/RDS%20running%20instance.png)  
![RDS Stack Output](screenshots/rds-ouput-stack.png)

---

### 3. EC2 Stack (`ec2.yaml`)

- **Stack Name**: `jithin-ec2-stack`
- **Resources**: EC2 instance, security group allowing SSH
- **Command**:
```bash
aws cloudformation create-stack   --stack-name jithin-ec2-stack   --template-body file://templates/ec2.yaml   --capabilities CAPABILITY_NAMED_IAM
```

**Screenshots**:

![EC2 Stack Created](screenshots/ec2%20creation%20success.png)  
![Running EC2 Instance](screenshots/EC2%20running%20instance.png)  
![Key Pair Used](screenshots/key%20pair.png)  
![Security Groups](screenshots/security%20groups.png)  
![EC2 Stack Output](screenshots/ec2-output-stack.png)

---

## Notes

- The `aws/` folder is excluded via `.gitignore` to avoid committing sensitive CLI configuration.
- The `.pem` key file for EC2 access is retained locally and not pushed to GitHub.

---
## Author

- Student Name: Jithin Jyothi
- Student ID: 8876281  

---
