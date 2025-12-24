# AWS VPC with EC2 Nginx Server

This Terraform project deploys a complete AWS infrastructure for hosting an Nginx web server in a custom VPC with proper networking and security configurations.

## Architecture Overview

### Networking Components
- **VPC**: Custom Virtual Private Cloud with CIDR block `10.0.0.0/16`
- **Public Subnet**: `10.0.2.0/24` with auto-assign public IP enabled
- **Private Subnet**: `10.0.1.0/24` for future backend resources
- **Internet Gateway**: Provides internet connectivity to public resources
- **Route Table**: Routes public traffic (`0.0.0.0/0`) through the Internet Gateway

### Compute & Security
- **EC2 Instance**: `t3.micro` instance running Amazon Linux 2023 in the public subnet
- **Nginx Web Server**: Automatically installed and configured via `user_data` script
- **Security Group**: Allows HTTP traffic (port 80) from anywhere, with full egress access
- **Deployment Region**: Tokyo (`ap-northeast-1`)

## Features
- ✅ Fully automated nginx installation using `dnf` package manager
- ✅ Public IP address automatically assigned to EC2 instance
- ✅ HTTP access enabled through security group rules
- ✅ Nginx configured to start automatically on boot
- ✅ Output values provide instant access to server IP and URL

## Usage

```bash
# Initialize Terraform
terraform init

# Preview changes
terraform plan

# Deploy infrastructure
terraform apply
```

## Access the Server

After deployment, access the nginx server at the public IP address displayed in the outputs.

## Outputs

- `instance_public_ip`: The public IP address of the EC2 instance
- `instance_url`: Direct HTTP URL to access the Nginx server

## Clean Up

```bash
terraform destroy
```
