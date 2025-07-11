
A **module** in Terraform is a container for multiple resources that are used together. Modules can be:

- **Local**: in a subfolder.
- **Remote**: GitHub, Terraform Registry, etc.


Basic Structure
File Tree Example:
```
main.tf
modules/
└── s3_bucket/
    ├── main.tf
    ├── variables.tf
    └── outputs.tf
```


Inside the module (`modules/s3_bucket/`)
main.tf
```
resource "aws_s3_bucket" "this" {
  bucket = var.bucket_name
  acl    = "private"
}
```

variables.tf
```
variable "bucket_name" {
  type = string
}
```

outputs.tf
```
output "bucket_id" {
  value = aws_s3_bucket.this.id
}
```


Calling the module (`main.tf` in root)
```
provider "aws" {
  region = "us-east-1"
}

module "my_bucket" {
  source      = "./modules/s3_bucket"
  bucket_name = "stanley-test-bucket"
}
```