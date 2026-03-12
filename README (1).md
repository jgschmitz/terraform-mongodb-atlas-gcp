# Terraform MongoDB Atlas on GCP

Terraform configuration for provisioning a **MongoDB Atlas cluster on
Google Cloud Platform (GCP)** along with core Atlas resources such as a
project, database user, and IP access list.

This repository demonstrates how to manage **MongoDB Atlas
infrastructure using Terraform**.

------------------------------------------------------------------------

## Architecture

This configuration provisions the following resources in MongoDB Atlas:

-   Atlas Project
-   MongoDB Atlas Cluster (GCP)
-   Database User
-   Network Access List / IP Whitelist

Terraform uses the **MongoDB Atlas Terraform Provider** to manage these
resources.

------------------------------------------------------------------------

## Prerequisites

Before using this configuration you need:

-   Terraform ≥ 1.0
-   MongoDB Atlas account
-   MongoDB Atlas API keys
-   GCP account (for cluster hosting)

Generate Atlas API keys:

Atlas Console → Organization Settings → Access Manager → API Keys

Export credentials as environment variables:

``` bash
export MONGODB_ATLAS_PUBLIC_KEY="your-public-key"
export MONGODB_ATLAS_PRIVATE_KEY="your-private-key"
```

------------------------------------------------------------------------

## Repository Structure

    .
    ├── provider.main.tf        # Terraform provider configuration
    ├── provider-variables.tf   # Provider credential variables
    ├── atlas-main.tf           # Atlas resources
    ├── atlas_variables.tf      # Cluster + project variables
    ├── terraform-tfvars.tf     # Default variable values

------------------------------------------------------------------------

## Quick Start

Clone the repository:

``` bash
git clone https://github.com/jgschmitz/terraform-mongodb-atlas-gcp.git
cd terraform-mongodb-atlas-gcp
```

Initialize Terraform:

``` bash
terraform init
```

Preview infrastructure changes:

``` bash
terraform plan
```

Deploy infrastructure:

``` bash
terraform apply
```

Destroy resources when finished:

``` bash
terraform destroy
```

------------------------------------------------------------------------

## Example terraform.tfvars

``` hcl
atlas_org_id           = "YOUR_ORG_ID"
atlas_project_name     = "example-project"
atlas_region           = "us-central1"
cluster_instance_size  = "M10"
db_username            = "app-user"
whitelist_list_cidr    = ["0.0.0.0/0"]
```

------------------------------------------------------------------------

## Resources Created

Running Terraform will provision:

-   MongoDB Atlas project
-   MongoDB cluster running on GCP
-   Database user
-   IP access list entry

------------------------------------------------------------------------

## Security Notes

-   Never commit API keys or secrets
-   Use environment variables or a secret manager
-   Restrict IP access lists whenever possible

------------------------------------------------------------------------

## References

-   MongoDB Atlas Terraform Provider
-   MongoDB Atlas API Documentation
-   Terraform Registry

------------------------------------------------------------------------

## Repository Status

⚠️ This repository was originally created as an experiment / reference
implementation.\
Some Terraform provider versions or patterns may be outdated.

------------------------------------------------------------------------

## License

MIT
