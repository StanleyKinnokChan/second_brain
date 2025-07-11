
```
variable "region" {
  description = "AWS region to deploy resources"
  type        = string
  default     = "us-west-1"
}
```

It can be referenced by other blocks
```
provider "aws" {
  region = var.region
}
```

It can be set as default and override later
```
default = "us-west-1"
```

Create a file named `terraform.tfvar`. Terraform automatically loads this file.
```
region = "eu-west-1"
```

Use `-var` flag on CLI
```
terraform apply -var="region=eu-west-2"
```

Use environment variable
```
export TF_VAR_region="ap-southeast-1"
terraform apply
```

To check if your variable was picked up, use output block. Values will show up after `terraform apply`
```
output "chosen_region" {
  value = var.region
}
```