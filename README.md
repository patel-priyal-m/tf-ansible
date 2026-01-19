# Terraform + Ansible Docker Deployment

Automated infrastructure provisioning and Docker deployment on AWS EC2 using Terraform and Ansible.

## Overview

- **Terraform**: Creates AWS infrastructure (VPC, EC2, security groups)
- **Ansible**: Installs Docker and deploys containerized applications
- **Automated**: Single command deployment from infrastructure to running containers

## Prerequisites

- AWS account with credentials configured
- Terraform installed
- Ansible installed
- SSH key pair

## Quick Start

1. Update `terraform/terraform.tfvars` with your values
2. Update `ansible/vars` with your Docker credentials
3. Run deployment:

```bash
cd terraform
terraform init
terraform apply -auto-approve
```

The provisioner automatically:
- Updates Ansible hosts file with EC2 IP
- Runs Ansible playbook to install Docker
- Deploys containers from docker-compose

## Structure

```
.
├── terraform/          # Infrastructure as Code
│   ├── main.tf
│   └── terraform.tfvars
├── ansible/           # Configuration Management
│   ├── deploy-docker.yaml
│   ├── hosts
│   └── vars
├── docker-compose.yml # Container definitions
└── monitor.html      # Monitoring page
```

## Services Deployed

- **Web App**: Your custom application on port 80
- **Redis**: Cache service
- **Monitor**: Status page on port 8080

## Cleanup

```bash
cd terraform
terraform destroy -auto-approve
```
