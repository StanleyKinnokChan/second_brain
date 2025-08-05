
A module is a container for related resources that are used together. They are the primary way to package and reuse configurations.
- **Improve organization:** by breaking large configuration into logical units for reuse
- **Easier collaboration:** standardize building block for other to use
- **Consistent pattern:** Enforcing naming conversion/ security control


---
### Structure
- Each modules basically consists of (1) main.tf, (2) variables.tf and (3) outputs.tf
- A parent module reference and configures other modules, child module is the reusable component being called
- Modules can be retrieved from a registry, a repo, or stored locally.

##### Inside the main.tf of a Parent/ Root/ Calling Module

**Source:**
**github:** "git::https://github.com/terraform-aws-modules/terraform-aws-vpc.git?ref=v5.12.0"
**terraform registry:** "terraform-aws-modules/vpc/aws"
**local folder:** "../../modules/module1_folder"
```
module "custom_name_foo" {  # calling child module
	source="teeraoform-aws-modules/vpc/aws"  #where the child module located?

	variable_name1 = variable_value1  # values that pass to the child
	variable_name2 = variable_value2
	variable_name3 = variable_value3
	...
}

output "vpc_id" {
	module.custom_name_foo.vpc_id  # which get the output value from the child
}

```

##### Inside the main.tf of a child module, just list the resource and variable
```
variable "variable_name1" {
...
}

variable "variable_name2" {
...
}

resource "label" "label2" {
....
}

resource "label" "label2" {
....
}


output "vpc_id" {   # usually exist so it can pass the argument back to parent
	value = aws_vpc.vpc.id
}

```


General step:
1. Parent use module block to call child module, which defines the child module location and variables needs passing to child
2. Child contains resources and create them using the variable from parent and itself
3. Child sends output values back to parent module
4. Parent use these output values for other resource creation, or display them on console.  

---
### Module Versioning
-  To specify the version, just point to the version in the registry
- When need to change the version, change the version value and run `terraform init -upgrade`
```
variable "cidr_block" {
  type    = string
  default = "192.168.0.0/16"
}

module "vpc" {
  source  = "terraform-aws-modules/vpc/aws"
  version = "5.12.0"  

  cidr = var.cidr_block
}

```