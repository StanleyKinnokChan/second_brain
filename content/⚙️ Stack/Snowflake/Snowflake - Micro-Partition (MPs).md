---
title: 
tags:
  - Snowflake
---
All data in Snowflake tables is automatically divided into micro-partitions, which are contiguous units of storage. Each micro-partition contains between 50 MB and 500 MB of uncompressed data

Snowflake stores metadata about all rows stored in a micro-partition, including:
- The range of values for each of the columns in the micro-partition
- The number of distinct values
- Additional properties used for both optimization and efficient query processing.

The micro-partition metadata maintained by Snowflake enables precise pruning of columns in micro-partitions at query run-time, including columns containing semi-structured data. In other words, a query that specifies a filter predicate on a range of values that accesses 10% of the values in the range should ideally only scan 10% of the micro-partitions.


>[!tip] Tips / Intuition
> Micro-partitions are immutable, it cannot be changed once it is created. New micro-partition are added for new data loads in.
> 
> It is a not problem when new data loaded in create new partition (e.g. time series). but if the operation consists of many DML (e.g. updates/ deletes). This will affect the performance

To improve the performance of micro-partitions, we ca use [[Snowflake - Clustering]]


