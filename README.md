Terraform MongoDB Atlas on GCP

Terraform configuration for provisioning a MongoDB Atlas cluster on Google Cloud Platform (GCP) along with basic Atlas resources such as a project, database user, and network configuration.

This repo demonstrates how to manage MongoDB Atlas infrastructure as code using Terraform.

Architecture

This Terraform configuration provisions the following resources in MongoDB Atlas:

Atlas Project

MongoDB Atlas Cluster (GCP)

Database User

Network Access List / IP Whitelist

Optional network peering configuration

Terraform uses the MongoDB Atlas provider to create and manage these resources.

Prerequisites

Before using this configuration you need:

Terraform ≥ 1.0

MongoDB Atlas account

MongoDB Atlas API keys

GCP account (if creating networking resources)

Generate Atlas API keys from:

Atlas Console → Organization Settings → Access Manager → API Keys

Export credentials as environment variables:

export MONGODB_ATLAS_PUBLIC_KEY="your-public-key"
export MONGODB_ATLAS_PRIVATE_KEY="your-private-key"
Repository Structure
.
├── provider.main.tf        # Terraform provider configuration
├── provider-variables.tf   # Provider credentials variables
├── atlas-main.tf           # Atlas resources
├── atlas_variables.tf      # Cluster and project variables
├── terraform-tfvars.tf     # Default variable values
Quick Start

Clone the repository:

git clone https://github.com/jgschmitz/terraform-mongodb-atlas-gcp.git
cd terraform-mongodb-atlas-gcp

Initialize Terraform:

terraform init

Review the infrastructure plan:

terraform plan

Deploy resources:

terraform apply

Destroy resources when finished:

terraform destroy
Configuration

Example terraform.tfvars:

atlas_org_id           = "YOUR_ORG_ID"
atlas_project_name     = "example-project"
atlas_region           = "us-central1"
cluster_instance_size  = "M10"
db_username            = "app-user"
whitelist_list_cidr    = ["0.0.0.0/0"]
Example Resources Created

Terraform will create:

Atlas project

MongoDB cluster in GCP

Database user with generated password

IP access list entry

Security Notes

Do not commit API keys or secrets

Use environment variables or a secrets manager

Restrict IP access lists where possible

Useful References

MongoDB Atlas Terraform Provider

Atlas API Documentation

Terraform Registry

License

MIT

💡 If you're doing a pass over old repos, I’d also add a short banner like:

⚠️ This repository was created as an experiment / reference implementation.
It may use outdated Terraform provider versions.
