---
title: Terraform block - variables
tags:
  - terraform
---


### Variables and Usage

variables.tf, default can be overwritten later
```

variable "region" {
  description = "AWS region to deploy resources"
  type        = string
  default     = "us-west-1"
}
```

It can be referenced by other blocks, via var.<variable_name>
```
provider "aws" {
  region = var.region
}
```


------
### Override

Create a file named `terraform.tfvar`. [[Terraform]] automatically loads this file and overwrite the variable's default values in variables.tf
```
region = "eu-west-1"
```


Use environment variable, with a format TF_VAR_XXX, terraform will search for the env as variable
```
export TF_VAR_region="ap-southeast-1"
terraform apply
```

Use `-var` flag on CLI
```
terraform apply -var="region=eu-west-2"
```

##### Order by Precedence
- Command Line Flags (higest)
- *.auto.tfvars files (for HTTP)
- *.tfvars files
- Env variable (TF_VAR_xxx)
- Variable block defaults
------
### Output Variable

To check if your variable was picked up, use output block. Values will show up after `terraform apply`
```
output "chosen_region" {
  value = var.region
}
```



https://developer.hashicorp.com/terraform/language/values/variables