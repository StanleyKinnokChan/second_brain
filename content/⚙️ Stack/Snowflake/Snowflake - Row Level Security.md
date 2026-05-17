---
title: Snowflake - Row Level Security
tags:
  - snowflake
---

- determine which rows to return in the query result based on the policy

Let's say we have mapping table like:

| sales_manager         | region  |
| --------------------- | ------- |
| `sales_manager_role1` | `East`  |
| `sales_manager_role1` | `West`  |
| `sales_manager_role2` | `North` |
| `sales_manager_role2` | `South` |
| `sales_manager_role3` | `East`  |
we can create logic in the policy and apply it in the target table. 
In the filter condition below, the viewer current role have to be `sales_executive_role` (then returns true for all role), or the current role exist in the mapping table, filtering by regions

```
--define ROW ACCESS POLICY

CREATE OR REPLACE ROW ACCESS POLICY security.sales_policy
AS (sales_region varchar) RETURNS BOOLEAN ->
  'sales_executive_role' = CURRENT_ROLE()
    OR EXISTS (
      SELECT 1 FROM salesmanagerregions
        WHERE sales_manager = CURRENT_ROLE()
        AND region = sales_region
    )
;

--Apply ROW ACCESS POLICY
ALTER TABLE sales_data
  ADD ROW ACCESS POLICY security.sales_policy ON (sales_region);

```

