---
title: 
tags:
  - spark
---
Repartition will incur a full shuffle of the data, regardless of whether one is necessary. 
Coalesce reduce the partitions, no re-shuffle occur.


```
# check number of partition of current df
df.rdd.getNumPartitions()

# print the rows in each partitions (check data skew)
df.rdd.mapPartitions(lambda x: [sum(1 for _ in x)]).collect()

# repartition can be done with number or column, or combined
df.repartition(5)
df.repartition(col("DEST_COUNTRY_NAME"))
df.repartition(5, col("DEST_COUNTRY_NAME"))

# coalesce
df.repartition(5, col("DEST_COUNTRY_NAME")).coalesce(2)
```