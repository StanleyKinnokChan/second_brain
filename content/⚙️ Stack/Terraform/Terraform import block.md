

Terraform brings the existing resources into Terraform management. 
 - defined the resources and import block, they are linked to each other
```
resource "aws_s3_bucket" "imported" {
  bucket = "stanawsbucket7425"
}

import {
  to = aws_s3_bucket.imported
  id = "stanawsbucket7425"
}
```
- use import command to bring they into terraform
```
#e.g.
terraform import aws_s3_bucket.imported stanawsbucket7425
```
- by using `terraform plan`/ `terraform apply`, the console indicates No changes, which approve it has been included in terraform
- After importing, you can use `terraform show -no-color > imported.txt` to capture the imported details, which is handy to migrate them into resource block afterwards