---
title: Terraform meta-argument
tags:
  - terraform
---

Special arguments that modify, manages, and structures multiple resources
## **count**
- Allows you to specify a number of instances for a resource. Example: Deploying five virtual machines with the same configurations 
- assigns an index to reference each instance
- reference the resource using `<type>.<name>[index]`
```
variable "vm_count" {
  type    = number
  default = 3
}

resource "azurerm_virtual_machine" "example" {
  count               = var.vm_count  # once defined count, can use count.index
  name                = "vm-${count.index}"  # avoid same name error
  location            = "East US"
  resource_group_name = "my-resource-group"
  vm_size             = "Standard_D2s_v3"

  os_profile {
    computer_name  = "vm-${count.index}"
    admin_username = "adminuser"
  }

  # You would also need os_profile_linux_config or windows_config,
  # network_interface_ids, and storage_* blocks to make this complete.
}
```
## **for_each**
Lets you create multiple resources dynamically from a map or set variable. Example: Deploying three VMS with different names instead of the same
- similar to count, but pulls in values from a map or set rather than a fixed number
- each resource get a unique key as a reference instead of arbitrary index
- ideal for managing unique configurations => stable even a resource is deleted
```
variable "vms" {
  type = map(string)
  default = {
    vml   = "Standard_B2ms"
    vm2   = "Standard_D2s_v3"
    vm3   = "Standard_D4s_v3"
  }
}

resource "azurerm_virtual_machine" "vm" {
  for_each            = var.vms  # point for_each to the map/set variable

  name                = each.key # call the key/value by using each.key/value
  location            = "East US"
  resource_group_name = "my-resource-group"
  vm_size             = each.value


...
}

```

## **depends_on**
Implicitly [[Terraform]] will try its best to figure out the dependency. This "depends_on" allow us to explicitly define that a resource must be created before another. 
- Ensure correct provisioning order
- prevents race conditions for deployments
Example: Ensure a database is provisioned before an app server
```
resource "aws_db_instance" "db" {
  identifier             = "imydb"
  engine                 = "mysql"
  instance_class         = "db.t3.micro"
  allocated_storage      = 20
  username               = "admin"
  password               = "SuperSecurePassword123!"
  skip_final_snapshot    = true
}

resource "aws_instance" "app_server" {
  ami           = "ami-abcdef1234567890"
  instance_type = "t2.micro"

  depends_on = [
    aws_db_instance.db,
    aws_s3_bucket.logs,
    aws_iam_role.app_role
  ]
}
```
## **provider**
Specify what provider configuration to use Example: Assign resources to use a different provider block mapped to a second region 
- explicitly assigns a resource to a specific provider config
- most often used for multi-cloud or multi account deployments (e.g. dev/ prod)
- Uses the `provider = <provider_alias>`, then the resource will be deployed using that provider block

Noted: If alias isn't provided, that block would be the default provider

example - dev/ prod in different regions
```
provider "aws" {
  alias  = "dev"
  region = "us-east-1"
}

provider "aws" {
  alias  = "prod"
  region = "us-west-1"
}

resource "aws_s3_bucket" "dev_bucket" {
  provider = aws.dev
  bucket   = "my-dev-bucket"
}

resource "aws_s3_bucket" "prod_bucket" {
  provider = aws.prod
  bucket   = "my-prod-bucket"
}
```
## **lifecycle**
Control how [[Terraform]] manages the lifecycle of the resource Example: Protect critical infrastructure or ensure that [[Terraform]] doesn 't replace resources unnecessarily
- protect resources/ avoid changes
- option include 
	1. `prevent_destroy` (bool):
		- a safe lock
		- setting of the previous run is saved in the state file, when the next run when the tf file has no that resource or requires replacement, it will throw an error
		  
	2. `create_before_destroy` (bool): 
		- By default, when there is changes terraform destroy the object first then recreate the resource with new config
		- this option changes the order
		  
	3. `ignore_changes` (list of attributes):
		- ignore the changes outside terraform (e.g. after manually change the config of the terraform-created resource)
		  
	4. replace_triggered_by (list of resource/ attribute)
		- force a **resource to be replaced** (destroyed and re-created) **when another resource or attribute changes**, even if the resource itself hasn't changed