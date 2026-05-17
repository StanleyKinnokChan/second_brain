---
title: Stages
tags:
  - spark
---
Spark, a **stage** is a group of tasks that can be executed in parallel without requiring data to be shuffled between nodes.
= a **chunk of the job that runs in one “step”**, where Spark can process data locally on each partition.

Shuffle Causes a New Stage:
- `groupBy`
- `reduceByKey`
- `join`
- `distinct`
- `repartition`
- `sort`
