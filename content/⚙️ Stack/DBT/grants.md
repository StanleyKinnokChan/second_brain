---
title: 
tags:
  - dbt
---
You can use the `grants` field to set permissions or grants for a resource. When you `run` a model, `seed` data, or `snapshot` a dataset, dbt will run `grant` and/or `revoke` statements to ensure that the permissions on the database object match the `grants` you have configured on the resource

Grants have two key components:

1. **Privilege:** A right to perform a specific action or set of actions on an object in the database, such as selecting data from a table.
2. **Grantees**: One or more recipients of granted privileges. Some platforms also call these "principals." For example, a grantee could be a user, a group of users, a role held by one or more users (Snowflake), or a service account (BigQuery/GCP).

e.g. grants user_a & b with `select` privilege
```
models:  
	+grants: # In this case the + is not optional, you must include it for your project to parse.  
	select: ['user_a', 'user_b']
```

**Grant config inheritance for specific model**
Overwrote: only user_c
```
{{ config(grants = {'select': ['user_c']}) }}
```
Additive: user_a, user_b, user_c
```
{{ config(+grants = {'select': ['user_c']}) }}
```