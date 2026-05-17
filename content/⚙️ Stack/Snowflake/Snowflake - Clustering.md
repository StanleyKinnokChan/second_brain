---
title: Snowflake - Clustering
tags:
  - snowflake
---

Without clustering, [[Snowflake]] **does not** actively optimize the distribution of data across [[Snowflake - Micro-Partition (MPs)]] — it’s essentially “append-only in the order data arrives.”

Clustering change the distribution of data across micro-partitions so that the data with close/ same values can collocate together within the micro-partition. 


#### Two Important Concepts:
### **1️⃣ Cluster Depth**
- Measures **how many MPs a single key value spans on average**.
- Calculated by MPs containing the key/ Total no. of MPs
- Low depth → the value is concentrated in few micro-partitions → efficient pruning.
- High depth → the value is spread across many partitions → more scanning required.
- for discrete values (ID, categories)

### **2️⃣ Cluster Overlap**
- Measures **how much the key value ranges of micro-partitions overlap**.
- Calculated by Range Overlap across MPs/ Total Range
- Low overlap → each micro-partition covers a tight, distinct range of values → pruning works well.
- High overlap → partitions cover overlapping key ranges → queries read more MPs than necessary.
- for ordered (date, numeric)

To view/monitor the clustering metadata for a table, [[Snowflake]] provides the following system functions:
- [SYSTEM$CLUSTERING_DEPTH](https://docs.snowflake.com/en/sql-reference/functions/system_clustering_depth)
- [SYSTEM$CLUSTERING_INFORMATION](https://docs.snowflake.com/en/sql-reference/functions/system_clustering_information) (including clustering depth)