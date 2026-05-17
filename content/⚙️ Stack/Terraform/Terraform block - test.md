---
title: Terraform block - test
tags:
  - terraform
---


Used in [[Terraform test]]

The optional `test` block defines the configuration of the test file, allowing you to configure how the framework executes its runs. The block has the following fields:

```
# with_config.tftest.hcl
test {
  parallel = true
}
```


|Field or Block Name|Description|Default Value|
|---|---|---|
|`parallel`|An optional boolean attribute. If `true`, [[Terraform]] executes all eligible `run` blocks simultaneously. Refer to [Parallel execution](https://developer.hashicorp.com/terraform/language/tests#parallel-execution) for more information.|`false`


https://developer.hashicorp.com/terraform/language/tests