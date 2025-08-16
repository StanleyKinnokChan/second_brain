---
title: 
tags:
  - Snowflake
---
Snowflake caches and persists the query results for every executed query. This can be used to great effect to dramatically reduce the time it takes to get an answer.  
  
Typically, query results are reused if _**all**_ of the following conditions are met:

- The user executing the query has the necessary access privileges for all the tables used in the query.
- The new query syntactically matches the previously-executed query.
- The table data contributing to the query result has not changed.
- The persisted result for the previous query is still available.
- Any configuration options that affect how the result was produced have not changed.
- The query does not include functions that must be evaluated at execution (e.g. CURRENT_TIMESTAMP()).
- The table’s micro-partitions have not changed (e.g. been re-clustered or consolidated) due to changes to other data in the table.


Noted that:
- the cache expires after 24 hours
- 