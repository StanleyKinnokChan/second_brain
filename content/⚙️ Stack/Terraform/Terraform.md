
Terraform is an open-source Infrastructure as Code (IaC) tool by HashiCorp that lets you define, provision, and manage infrastructure across cloud providers like AWS, Azure, GCP, and more using a declarative configuration language (`.tf` files).

---
### Configuration
###### Block = type, label & Body

A block structure:
```
type "label1" "label2" {
	argument_name1 = argument_value1
	inner_type {
		argument_name2 = argument_value2
	}
}
```


---
### Common command

`terraform init`
- Initializes a working directory with Terraform configuration files. Downloads provider plugins.
- -upgrade updates version of module/ providers

`terraform plan`
- Shows a preview of what changes Terraform will make without applying them.

`terraform apply`
- Applies the changes required to reach the desired state defined in your `.tf` files.
- -auto-approve avoid the double confirmation
- -replace="ADDRESS" replace that specified resource by destroy and recreate (legacy taint)

`terraform destroy`
- Tears down all resources defined in the configuration.
- -target="ADDRESS" destroy that specified resource without touching the tf script

`terraform validate`
- Checks whether the configuration is syntactically valid.

`terraform fmt -recursive` 
- Formats `.tf` files in the current directory. -recursive for all subdirectory as well

`terraform show`
- Displays the contents of the state file.

`terraform import <resource_type>.<resource_name> <resource_id>`
- Brings existing infrastructure into Terraform's state.

`terraform output`
- Shows the output values defined in the configuration.

`terraform state`
- Manage state manually
- -list list out all the existing resources

