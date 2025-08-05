Terraform must store state about your managed infrastructure and configuration. This state is used by Terraform to map real world resources to your configuration, keep track of metadata, and to improve performance for large infrastructures.

This state is stored by default in a local file named "terraform.tfstate"

----
### State locking 
- prevents multiple users or processes from making concurrent changes to the same state file
##### Details:

- When you run commands like `terraform plan` or `terraform apply`, Terraform **locks** the state.
- Once the operation finishes, it **releases** the lock.
- If another operation tries to run while the state is locked, it will wait (or error out, depending on the backend).

You can manually disable locking (not recommended in production) with `terraform apply -lock=false`

Manually unlock the state for the defined configuration.
```
terraform force-unlock [options] LOCK_ID
```
---
#### Remove state
- to forget a resource **without deleting it**
```
terraform state rm [address]
```

**Use Case**
- - It’s now managed manually or by another tools
- You’re splitting monolith into multiple Terraform workspaces/stacks
- If someone deletes a resource manually (e.g., EC2) but it's still in the state, Terraform might behave unpredictably.
- If a resource is wrongly imported or needs re-import,
- Fix the drift or errors. 

---
### Other command 

State list
List out all the address of resource in state
```
terraform state list
```

State show
show all the config of resource in state
```
terraform state show
```

State pull
- **Purpose**: Fetches the current state file from the backend and prints it to `stdout`.
- **Use case**: For debugging, inspection, or manual state manipulation.
```
terraform state pull
```

State push
- **Purpose**: Uploads a local `.tfstate` file to the backend, overwriting the current state.
- **Use case**: After manual editing or recovery of a state file.
```
terraform state push
```
