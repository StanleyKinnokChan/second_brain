---
title: 
tags:
  - Snowflake
---
A dynamic table in Snowflake is a table that automatically refreshes its data based on changes in the underlying source tables or queries. It’s designed to maintain fresh data with minimal manual intervention.

```
CREATE OR REPLACE DYNAMIC TABLE my_dynamic_table
  TARGET_LAG = '20 minutes'
  WAREHOUSE = my_warehouse
  [REFRESH_MODE = auto]
  [INITIALIZE = on_create]
  AS
    SELECT product_id, product_name FROM staging_table;
```

**Target Lag:** 
- This is the maximum time you want the data in the dynamic table to lag behind the source data. "should be no more than x hours behind the orders table". 
- The schedule may happen within or exceed the target lag
- If it is set as "Downstream", then the table only refreshed when the downstream table to refresh, or triggered manually or by task

You can chain the dynamic table to build a pipeline on schedule
Source_table -> Dymamic_table_A ("downstream") -> Dynamic_table_B ("1 hour")