---
title: Storage level (RDD Persistence)
tags:
  - spark
  - exam
---
3 main focus: 
1. memory, disk, or both
2. replcate on rwo cluster node or not
3. serieralize or not (for java/ scala)

| Storage Level                             | Meaning                                                                                                                                                                                                                                                               |
| ----------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| MEMORY_ONLY                               | Store RDD as deserialized Java objects in the JVM. If the RDD does not fit in memory, some partitions will not be cached and will be recomputed on the fly each time they're needed. This is the default level.                                                       |
| MEMORY_AND_DISK                           | Store RDD as deserialized Java objects in the JVM. If the RDD does not fit in memory, store the partitions that don't fit on disk, and read them from there when they're needed.                                                                                      |
| MEMORY_ONLY_SER  <br>(Java and Scala)     | Store RDD as _serialized_ Java objects (one byte array per partition). This is generally more space-efficient than deserialized objects, especially when using a [fast serializer](https://spark.apache.org/docs/latest/tuning.html), but more CPU-intensive to read. |
| MEMORY_AND_DISK_SER  <br>(Java and Scala) | Similar to MEMORY_ONLY_SER, but spill partitions that don't fit in memory to disk instead of recomputing them on the fly each time they're needed.                                                                                                                    |
| DISK_ONLY                                 | Store the RDD partitions only on disk.                                                                                                                                                                                                                                |
| MEMORY_ONLY_2, MEMORY_AND_DISK_2, etc.    | Same as the levels above, but replicate each partition on two cluster nodes.                                                                                                                                                                                          |
| OFF_HEAP (experimental)                   | Similar to MEMORY_ONLY_SER, but store the data in [off-heap memory](https://spark.apache.org/docs/latest/configuration.html#memory-management). This requires off-heap memory to be enabled.                                                                          |

ref: https://spark.apache.org/docs/latest/rdd-programming-guide.html#rdd-persistence