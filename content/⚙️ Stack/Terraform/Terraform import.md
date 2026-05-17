---
title: Terraform import
tags:
  - terraform
---


1. Add [[Terraform block - import]]
2. Plan and generate configuration
   `terraform plan -generate-config-out="generated_resources.tf"`
3. Review the generated configuration and update the abstract resources in the main scripts needed.
4. run `terraform apply` to import your infrastructure
5. delete the import block

https://developer.hashicorp.com/terraform/language/import/generating-configuration