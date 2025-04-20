# AWS Infrastructure with Terraform

This repository contains a Terraform configuration to provision AWS infrastructure. It sets up a VPC, Subnet, Internet Gateway, Route Table, Security Group, Elastic IP, and an EC2 instance hosting a Dockerized web application.

---

## 🚀 Features

- **VPC**: Custom Virtual Private Cloud (CIDR: `10.0.0.0/16`).
- **Subnet**: Public subnet (CIDR: `10.0.1.0/24`) in the `ap-south-1a` availability zone.
- **Internet Gateway**: Enables public internet access.
- **Route Table**: Routes traffic via the Internet Gateway.
- **Security Group**: Allows inbound traffic for HTTP (80), HTTPS (443), and SSH (22).
- **Elastic IP**: Static public IP associated with the EC2 instance.
- **EC2 Instance**: `t2.micro` instance running a Dockerized web application.

---

## 🛠️ Prerequisites

Before you begin, ensure you have the following:

1. **AWS CLI**  
   - Install the AWS CLI by following the [installation guide](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html).
   - Configure it with your AWS credentials:
     ```bash
     aws configure
     ```
     You will need to provide:
     - **AWS Access Key ID**
     - **AWS Secret Access Key**
     - **Default region name** (e.g., `ap-south-1`).

2. **Terraform**  
   Install Terraform. Refer to the [official guide](https://developer.hashicorp.com/terraform/tutorials/aws-get-started/install-cli).

3. **Key Pair**  
   Ensure you have an existing EC2 key pair in AWS or create a new one. Update the `key_name` field in `main.tf` with your key pair name.

4. **Docker Hub Image**  
   Replace `yourdockerhubusername/imagesName` in the `user_data` section with your actual Docker Hub image name.

   My DockerHub image ```docker pull utkarshjain01/tf-infra```.

---

## 📂 Project Structure

- `main.tf`: Terraform configuration file containing all resources.

---

## 📋 Configuration Overview

### Terraform Resources

| Resource              | Details                                       |
|-----------------------|-----------------------------------------------|
| **VPC**               | CIDR: `10.0.0.0/16`                          |
| **Subnet**            | CIDR: `10.0.1.0/24`, Availability Zone: `us-east-2a` |
| **Internet Gateway**  | Provides internet access                     |
| **Route Table**       | Configured to route public traffic via Internet Gateway |
| **Security Group**    | Inbound rules for HTTP (80), HTTPS (443), SSH (22) |
| **Elastic IP**        | Static IP associated with the EC2 instance   |
| **EC2 Instance**      | `t2.micro`, Ubuntu 20.04, Dockerized app     |

---

## 🚀 Deployment Steps

Follow these steps to deploy the infrastructure:

1. **Clone the Repository**:
   ```bash
   git clone <repository-url>
   cd <repository-folder>

2. **Initialize Terraform:**
   ```bash
     terraform init

3. **Validate Configuration:**
   ```bash
    terraform validate

4. **Preview Chnages:**
   ```bash
     terraform plan

5. **Apply Configuration:**
   ```bash
     terraform apply
Confirm with ```yes``` when prompted.

6. **Access the Application:**
   + Retrieve the Elastic IP from the AWS Console or Terraform output.
   + Open a browser and navigate to ```public id address```.
  
## 🧹 Cleanup Resources

To destroy the created infrastructure:
```bash
terraform destroy
```
Confirm with ```yes``` when prompted.

## 🔧 Customization
Modify the availability_zone if ```us-east-2a``` is not in your region.
Replace ```yourdockerhubusername/tfinfradocker``` in ```user_data``` with your Docker image.
