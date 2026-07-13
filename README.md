# 🚀 Terraform MongoDB Atlas on Google Cloud

Provision a complete **MongoDB Atlas environment on Google Cloud Platform (GCP)** using **Terraform**.

This repository demonstrates Infrastructure as Code (IaC) best practices for deploying and managing MongoDB Atlas resources including projects, clusters, database users, and network access controls.

---

## ✨ Features

- 🏗️ Create a MongoDB Atlas Project
- ☁️ Deploy Atlas Clusters on Google Cloud
- 👤 Create Database Users
- 🔒 Configure IP Access Lists
- ⚙️ Fully declarative Infrastructure as Code
- 🔄 Easy to reproduce across Development, Test, and Production environments

---

# Architecture

```text
                     Terraform
                         │
                         ▼
             MongoDB Atlas Provider
                         │
     ┌───────────────────┼───────────────────┐
     ▼                   ▼                   ▼
Atlas Project      Atlas Cluster      Database User
     │
     ▼
Network Access List
```

---

# Repository Structure

```text
.
├── atlas-main.tf              # Atlas resources
├── atlas_variables.tf         # Project and cluster variables
├── provider.main.tf           # Terraform provider configuration
├── provider-variables.tf      # Atlas API credentials
├── terraform.tfvars           # Example variables
└── README.md
```

---

# Prerequisites

Before getting started, ensure you have:

- Terraform 1.0 or newer
- MongoDB Atlas Account
- MongoDB Atlas Organization API Keys
- Google Cloud account

---

# MongoDB Atlas API Keys

Generate API keys from:

```
Atlas
└── Organization Settings
    └── Access Manager
        └── API Keys
```

Export your credentials as environment variables.

```bash
export MONGODB_ATLAS_PUBLIC_KEY="YOUR_PUBLIC_KEY"
export MONGODB_ATLAS_PRIVATE_KEY="YOUR_PRIVATE_KEY"
```

---

# Quick Start

## Clone the Repository

```bash
git clone https://github.com/jgschmitz/terraform-mongodb-atlas-gcp.git

cd terraform-mongodb-atlas-gcp
```

## Initialize Terraform

```bash
terraform init
```

## Review the Deployment

```bash
terraform plan
```

## Deploy

```bash
terraform apply
```

Terraform will create all configured MongoDB Atlas resources.

---

# Destroy Resources

To remove all deployed infrastructure:

```bash
terraform destroy
```

---

# Example terraform.tfvars

```hcl
atlas_org_id         = "YOUR_ORG_ID"
atlas_project_name   = "terraform-demo"

atlas_region         = "us-central1"

cluster_instance_size = "M10"

db_username = "app-user"

whitelist_list_cidr = [
  "0.0.0.0/0"
]
```

---

# Resources Created

Running this configuration provisions:

| Resource | Description |
|----------|-------------|
| Atlas Project | Creates a MongoDB Atlas Project |
| Atlas Cluster | Deploys an Atlas Cluster on Google Cloud |
| Database User | Creates an application database user |
| IP Access List | Configures network access rules |

---

# Security Best Practices

- Never commit API keys to source control.
- Use environment variables or a secrets manager.
- Limit IP Access Lists to trusted CIDR ranges.
- Use least-privilege Atlas API keys.
- Store Terraform state securely (Terraform Cloud, GCS, etc.).

---

# Terraform Workflow

```text
terraform init
        │
        ▼
terraform plan
        │
        ▼
terraform apply
        │
        ▼
 MongoDB Atlas Resources
```

---

# Useful Documentation

- MongoDB Atlas Terraform Provider
- Terraform Registry
- MongoDB Atlas Documentation
- MongoDB Atlas Administration API

---

# Contributing

Contributions, bug reports, and feature requests are welcome.

Feel free to submit a Pull Request or open an Issue.

---

# License

Licensed under the MIT License.
