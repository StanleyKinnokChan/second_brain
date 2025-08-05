Configuring global config for terraform itself, allowing consistency across teams and environment
- terraform and provider versions
- backend config (state location)
- provider requirements

```
terraform {
  required_version = "~> 1.10.0"

  required_providers {
    aws = {
      source  = "hashicorp/aws"
      version = "5.87.0"
    }
  }

# store the state at s3
  backend "s3" {
    bucket = "prd-terraform-east-2"
    key    = "state/terraform.tfstate"
    region = "us-east-2"
  }
}
```
https://developer.hashicorp.com/terraform/language/terraform
---
### Version constraints
- required_version = "1.10.0"   # only 1.10.0
- required_version = "=> 1.10.0"  # all versions >= this version 1.11.0/ 1.12.0....
- required_version = "~> 1.10.0"  # all patches within the same versions, e.g. ok for 1.10.5, but no for 1.11.0

Use `terraform init -upgrade` to upgrade the the version, after modifying the version number

-----
The `backend` block inside terraform block defines where Terraform stores its [state](https://developer.hashicorp.com/terraform/language/state) data files, which is default as "local". (terraform.tfstate)

Example - save in S3:
```
terraform {
  backend "s3" {
    bucket = "" 
    key    = ""
    region = ""
    profile= ""
  }
}
```

https://developer.hashicorp.com/terraform/language/backend



