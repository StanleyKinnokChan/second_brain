# Stack Roles

- CFN creates physical resources when you create a stack
- CFN uses the **permissions** of the logged in identity, which means you **need permissions for AWS**
- it allow CFN assuming a role to gain the permissions (enable role separation)
- identity creating the stack..doesn’t need **resource permission** - only **PassRole**
    - the cloud creation team won’t have access to the resource, just creation

[[Stack Roles/Untitled.png]]
