#### Integration Testing
By default, each `run` block executes with `command = apply` instructing Terraform to execute a complete `apply` operation against your configuration. You are testing Terraform's core functionality by executing operations and validating the infrastructure Terraform creates.
#### Unit Testing
Replacing the `command` value with `command = plan` instructs Terraform to _not_ create new infrastructure for this `run` block. This allows test authors to validate logical operations and custom conditions within their infrastructure in a process analogous to .

https://developer.hashicorp.com/terraform/language/tests

---
### Composition of test
- discover of test files are based on their file extension: `.tftest.hcl` or `.tftest.json`
- Each test file contains the following root level attributes and blocks:
	- One to many [`run`](https://developer.hashicorp.com/terraform/language/tests#run-blocks) blocks.
	- Zero to one [`test`](https://developer.hashicorp.com/terraform/language/tests#test-block) blocks.
	- Zero to one [`variables`](https://developer.hashicorp.com/terraform/language/tests#variables) block.
	- Zero to many [`provider`](https://developer.hashicorp.com/terraform/language/tests#providers) blocks.
- By default, Terraform executes `run` blocks sequentially.
- Defining your `variables` and `provider` blocks first, at the beginning of the test file, is recommended

[[Terraform block - run]]: **core unit of test execution**
[[Terraform block - test]]: **test configuration**
[[Terraform block - variables]]: in testing file, it pas the variables to all run blocks (can be overridden by the local definition of variables in a run block)
[[Terraform block - providers]]: set or override the required providers within the main configuration from your testing files

---
#### Modules

The `module` blocks inside `run` blocks are used to orchestrate which modules to test, and are **not** the same as traditional Terraform modules used for organizing infrastructure resources.

---
#### Folder structure:

```
.
├── main.tf                    # Main configuration that uploads files to S3
├── file_count.tftest.hcl     # Test file with multiple run blocks
├── testing/
│   ├── setup/
│   │   └── main.tf           # Setup module to create S3 bucket
│   └── loader/
│       └── main.tf           # Loader module to validate S3 objects
└── data/
    └── files/
        ├── file_one.txt      # Sample file 1
        └── file_two.txt      # Sample file 2
```

`.tftest.hcl` file is located in the root directory, `terraform test` command should also be run at the root directory

setup module mainly used for setting up the resources that used for testing
loader module mainly used for retrieving the info of the resources using data block.

---
#### Variables

In standard work, the values of variables are declared by `.tfvar` file. However, during the test, Terraform retrieved from what defined in the `.tftest.hcl` files in the variables block with a specific value with **highest precedence**, and populate these values into the run block (could be further overridden) in the same file, down to the main script and the modules specified in the run block.

---
### Key Differences Between check and test

| Feature               | check Block                                | test Framework                              |
| --------------------- | ------------------------------------------ | ------------------------------------------- |
| **Purpose**           | Validate live infrastructure state.        | Test Terraform configurations in isolation. |
| **Defined In**        | .tf configuration files.                   | .tftest.hcl test files.                     |
| **Execution Command** | terraform plan or terraform apply.         | terraform test.                             |
| **Scope**             | Runtime validation of real infrastructure. | Pre-deployment testing in a sandbox.        |
| **Failure Behavior**  | Warnings by default; can fail with error.  | Fails the test suite, no impact on infra.   |
| **Use Case**          | Enforce compliance or invariants.          | Validate modules or configurations.         |
| **Environment**       | Runs against real infrastructure.          | Runs in a temporary, isolated environment.  |
| **Introduced In**     | Terraform 1.5 (enhanced in 1.8).           | Terraform 1.6.                              |



