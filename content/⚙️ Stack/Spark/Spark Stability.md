---
title: 
tags:
  - spark
  - exam
---
In Spark, the driver node is crucial for orchestrating the execution of the Spark application. If the driver node fails, the Spark application fails.

- Spark is designed to support the loss of any set of worker nodes.
- Spark will rerun any failed tasks due to failed worker nodes.
- Spark will recompute data cached on failed worker nodes.
- Spark will spill data to disk if it does not fit in memory.