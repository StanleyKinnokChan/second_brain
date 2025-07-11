
erraform is an open-source Infrastructure as Code (IaC) tool by HashiCorp that lets you define, provision, and manage infrastructure across cloud providers like AWS, Azure, GCP, and more using a declarative configuration language (`.tf` files).


Command command

`terraform init`
Initializes a working directory with Terraform configuration files. Downloads provider plugins.

`terraform plan`
Shows a preview of what changes Terraform will make without applying them.

`terraform apply`
Applies the changes required to reach the desired state defined in your `.tf` files.

`terraform destroy`
Tears down all resources defined in the configuration.

`terraform validate`
Checks whether the configuration is syntactically valid.

`terraform fmt`
Formats `.tf` files to canonical style.

`terraform show`
Displays the contents of the state file.

`terraform import <resource_type>.<resource_name> <resource_id>`
Brings existing infrastructure into Terraform's state.

`terraform output`
Shows the output values defined in the configuration.

`terraform taint <resource>`
Marks a resource for forced recreation on the next apply.

`terraform untaint <resource>`
Reverses a taint.

`terraform state`
Manage state manually:

