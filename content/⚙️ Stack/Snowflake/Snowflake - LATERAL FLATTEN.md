---
title: Snowflake - LATERAL FLATTEN
tags:
  - snowflake
---
TABLE(FLATTEN(...)) can operate independently. It can flatten a variant structure without needing a pre-existing table. The `TABLE` keyword allows the result of the `FLATTEN` function, which is typically a collection of key-value pairs, to be treated as a relation or a table within the SQL query

`LATERAL FLATTEN` is used when you need to flatten a variant column in a table and correlate the flattened output with each row of the original table. It implies a row-by-row evaluation and correlation. LATERAL FLATTEN acts on the context of the outer table, processing each row individually. So it essentially says: for each row in the source table, flatten the variant cell and link it back to source table