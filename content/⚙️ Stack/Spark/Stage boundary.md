---
title: Stage boundary
tags:
  - spark
  - exam
---
a stage represents a sequence of narrow transformations that can be executed without shuffling the entire data across partitions

Since data moves across nodes during shuffling, [[Spark]] cannot continue executing within the same stage—it must stop, wait for the shuffle to complete, and then **start a new stage** to process the shuffled data, before starting the next stage. The boundary between two stages is the the stage boundary

- **Narrow Dependencies (No Stage Boundary)**
    
    - Operations like **map, filter, and flatMap** do not require data to be shuffled across different nodes.
    - These operations can be pipelined together in the same stage.
- **Wide Dependencies (Stage Boundary)**
    
    - Operations like **groupBy, reduceByKey, join, and repartition** require a **shuffle** (redistribution of data across nodes).
    - When a **shuffle occurs**, [[Spark]] creates a **stage boundary**, meaning a new stage starts after the shuffle.