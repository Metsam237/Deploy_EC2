# Terraform VPC and EC2 Deployment

This project automates the deployment of an AWS VPC, subnet, security group, and EC2 instance using Terraform. It demonstrates skills in **cloud automation**, **infrastructure as code (IaC)**, and **AWS resource provisioning**.

## Features
- Provisions a VPC with a public subnet
- Configures a security group allowing SSH (port 22)
- Deploys an EC2 instance with a dynamic Amazon Linux AMI
- Modular Terraform code for reusability
- GitHub Actions CI/CD for linting and validation

## Prerequisites
- [AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html)
- [Terraform](https://developer.hashicorp.com/terraform/tutorials/aws-get-started/install-cli) (>= 1.5.0)
- [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
- An AWS account with configured credentials

## Project Structure
Organizing files properly ensures maintainability:
```plaintext
terraform-vpc-ec2/
├── modules/              # Reusable Terraform modules
│   ├── vpc/             # VPC-related resources
│   │   ├── main.tf
│   │   ├── variables.tf
│   │   └── outputs.tf
│   └── ec2/             # EC2-related resources
│       ├── main.tf
│       ├── variables.tf
│       └── outputs.tf
├── main.tf              # Root module calling sub-modules
├── variables.tf         # Global variables
├── terraform.tfvars     # User-specific variables (gitignored)
├── outputs.tf           # Global outputs
├── provider.tf          # AWS provider config
├── .github/             # GitHub-specific files
│   └── workflows/       # CI/CD pipeline (e.g., Terraform lint/validate)
│       └── terraform.yml
├── .gitignore           # Ignore unnecessary files
├── README.md            # Detailed project documentation
└── LICENSE              # Add a license (e.g., MIT) for professionalism
```



## Setup Instructions
Follow these steps to deploy the project:

1. **Clone the Repository**
   - Download the project from GitHub:
     ```bash
     git clone https://github.com/YOUR_USERNAME/terraform-vpc-ec2.git
     cd terraform-vpc-ec2
     ```

2. **Configure AWS CLI**
   - Ensure your AWS credentials are set up:
     ```bash
     aws configure
     ```
   - Enter your AWS Access Key, Secret Key, Region (e.g., `us-east-1`), and Output Format (e.g., `json`).

3. **Initialize Terraform**
   - Install dependencies and prepare the working directory:
     ```bash
     terraform init
     ```

4. **Deploy Resources**
   - Apply the Terraform configuration to create the VPC, subnet, security group, and EC2 instance:
     ```bash
     terraform apply -auto-approve
     ```

5. **Retrieve the EC2 Public IP**
   - Get the public IP address of the deployed EC2 instance:
     ```bash
     terraform output instance_public_ip
     ```

6. **(Optional) SSH into the Instance**
   - Use the public IP to connect (ensure you have a key pair configured):
     ```bash
     ssh -i your-key.pem ec2-user@PUBLIC_IP
     ```

7. **Clean Up**
   - Destroy all resources to avoid AWS charges:
     ```bash
     terraform destroy -auto-approve
     ```

## Usage
- Customize variables in `terraform.tfvars` (e.g., `aws_region`, `instance_type`) before applying, if needed. This file is gitignored for security.
- Validate deployment in the AWS Console or via SSH.

## Validation
- Check AWS Console for VPC, subnet, and EC2 resources.
- SSH into the instance using the public IP.

## CI/CD
- GitHub Actions runs `terraform fmt`, `init`, and `validate` on every push/PR.

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file.

---
Built with 🚀 by [Airvay](https://github.com/metsam237)

   
