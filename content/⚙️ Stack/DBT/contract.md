---
title: 
tags:
  - dbt
---
When the `contract` configuration is enforced, dbt will ensure that your model's returned dataset exactly matches the attributes you have defined in yaml:

- `name` and `data_type` for every column
- Additional [`constraints`](https://docs.getdbt.com/reference/resource-properties/constraints), as supported for this materialization and data platform


It ensures the model being delivered must have the specified columns and data types