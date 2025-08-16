---
title: 
tags:
  - Snowflake
---
## Common query problems identified by Query Profile

### “Exploding” joins
- can be observed by looking at the number of records produced by a Join operator, and typically is also reflected in Join operator consuming a lot of time.

### UNION without ALL
- A common mistake is to use UNION when the UNION ALL semantics are sufficient.
- These queries show in Query Profile as a UnionAll operator with an extra Aggregate operator on top (which performs duplicate elimination).

### Queries too large to fit in memory
- query processing engine will start _spilling_ the data to local disk. If the local disk space is not sufficient, the spilled data is then saved to remote disks.
- To alleviate this, use larger warehouse/ processing data in smaller batches

### Inefficient pruning
- The efficiency of pruning can be observed by comparing _Partitions scanned_ and _Partitions total_ statistics in the TableScan operators. If the former is a small fraction of the latter, pruning is efficient. If not, the pruning did not have an effect.