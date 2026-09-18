# DevOps Engineer Practical Challenge
## Production-Ready Application Deployment


## Architecture Overview

This project deploys a containerized Python Flask web application
on AWS EC2 using a fully automated DevOps pipeline.

## Tech Stack

| Component | Technology |
|-----------|------------|
| Application | Python Flask |
| Containerization | Docker |
| Infrastructure as Code | Terraform |
| CI/CD Pipeline | Jenkins |
| Cloud Provider | AWS (EC2, VPC, CloudWatch) |
| Version Control | GitHub |
| Monitoring | AWS CloudWatch |

---

## Prerequisites

Before deploying, make sure you have:

- AWS Account with IAM user and Access Keys configured
- AWS CLI installed and configured (`aws configure`)
- Terraform installed (v1.0+)
- Docker Desktop installed
- Git installed
- SSH key pair generated (`~/.ssh/id_rsa`)

---

## Deployment Steps

### 1. Clone the Repository
```bash
git clone https://github.com/Ezehsampson1/practical-challenge.git
cd practical-challenge
```

### 2. Provision Infrastructure with Terraform
```bash
cd terraform
terraform init
terraform plan
terraform apply
```
Note the output values — you'll need the EC2 public IP.

### 3. Access Jenkins
- Open browser: `http://<EC2_PUBLIC_IP>:8080`
- Unlock Jenkins using:
```bash
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

### 4. Configure Jenkins Pipeline
- Create a new Pipeline job
- Point it to this GitHub repository
- Use the Jenkinsfile in the root directory
- Click Build Now

### 5. Access the Application
Once the pipeline runs successfully:
- App: `http://<EC2_PUBLIC_IP>:5000`
- Health Check: `http://<EC2_PUBLIC_IP>:5000/health`

---

## 🔄 CI/CD Pipeline

The Jenkins pipeline consists of 5 automated stages:
