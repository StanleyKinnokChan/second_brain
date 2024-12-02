---
title: 
tags:
  - SQL
  - performance
---
General Step:
1. Generate explain plan for the SQL queries
2. Interpret the explain plan to identify the performance bottlenecks
3. Act by using right technique to improve the performance

Rule #1: If its linked by it, filtered by it, or sorted by it....index by it.

Technical list:
1. select column instead of all (avoid full table scanning)
2. 10. add index & partition (pruning)
3. pre-join data instead of joining same table repeatedly
4. minimize the use of distinct
5. Predicate pushdown (e.g. instead of having)
6. Use wildcards at the end of a phrase only
7. avoid using many OR for large dataset
8. avoid too many join
9. limit the row being return
10. sort data when needed
11. watch the execution plan (and statistic like disk, memory, network, process time, size)


