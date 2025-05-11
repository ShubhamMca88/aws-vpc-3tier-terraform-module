# AWS 3-Tier VPC with Public and Private Subnets

This Terraform project sets up a reusable 3-tier VPC architecture in AWS, consisting of public, application (private), and database (private) subnets across multiple Availability Zones.

---

## 🚀 Features

- Fully modular and reusable
- Public and private subnet separation
- NAT Gateway for outbound internet access from private subnets
- Internet Gateway for public subnet access
- Route tables and associations
- Descriptive resource tagging
- Environment-specific configurations (dev, staging, prod)

---

## 📁 Project Structure

```
.
├── main.tf
├── variables.tf
├── outputs.tf
├── vpc-module/
│   ├── main.tf
│   ├── variables.tf
│   └── outputs.tf
```

---

## 🔧 Required Inputs (terraform.tfvars)

```hcl
vpc_cidr = "10.0.0.0/16"

public_subnets = [
  "10.0.1.0/24",
  "10.0.2.0/24"
]

private_subnets = [
  "10.0.11.0/24",
  "10.0.12.0/24"
]

availability_zones = [
  "us-east-1a",
  "us-east-1b"
]

environment = "dev"
```

---

## 💻 Terraform Commands (in order)

```bash
# Initialize the working directory
terraform init

# Validate the configuration
terraform validate

# Show an execution plan
terraform plan -var-file="terraform.tfvars"

# Apply the changes
terraform apply -var-file="terraform.tfvars"

# Destroy all resources when no longer needed
terraform destroy -var-file="terraform.tfvars"
```

---

## 📤 Outputs

After successful deployment, the following outputs are available:

- `vpc_id` – The ID of the created VPC
- `public_subnets` – List of public subnet IDs
- `private_subnets` – List of private subnet IDs

---

## ✅ Prerequisites

- AWS CLI configured (`aws configure`)
- Terraform ≥ 1.0
- IAM user with VPC, subnet, NAT, and IGW permissions