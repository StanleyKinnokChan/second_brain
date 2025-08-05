
Terraform import block is a temporary tool used to bring an existing resource into Terraform's management by adding it to the state file, so that you didn't need to first destroy the existing resource when updating the resources. It should be removed guadually from the code and keep the code clean


 - defined the resources and import block, they are linked to each other
```
resource "aws_s3_bucket" "imported" {  # define a resouce abstractly
  bucket = "stanawsbucket7425"
}

import {
  to = aws_s3_bucket.imported # address of the defined Terraform resource
  id = "stanawsbucket7425" # real resource existing in the provider
}
```
- use import command to bring they into terraform
```
#e.g.
terraform import aws_s3_bucket.imported stanawsbucket7425
```
- by using `terraform plan`/ `terraform apply`, the console indicates No changes, which approve it has been included in terraform
- After importing, you can use `terraform show -no-color > imported.txt` to capture the imported details, which is handy to migrate them into resource block afterwards

- you can generate the resource block in a new file via `terraform plan -generate-config-out=PATH`