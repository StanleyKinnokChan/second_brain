---
title: 
tags:
  - spark
  - exam
---
## **`cache()` – Stores in Memory (Default Storage Level)**

✅ **Stores the DataFrame in memory (`MEMORY_AND_DISK`) for faster access.**  
✅ **No control over storage level** (always stored in RAM).  
✅ **Useful when the dataset fits into memory and needs to be reused multiple times.**

- Equivalent to `.persist(StorageLevel.MEMORY_ONLY)` (RAM only).
- If memory is insufficient, cached partitions are **recomputed** instead of being written to disk.
- On subsequent actions, Spark **retrieves the DataFrame from memory** instead of recomputing it.

## **`persist()` – Customizable Storage Level**

✅ **Allows different storage levels** (memory, disk, or both).  
✅ **Useful when memory constraints require spilling data to disk.**

- If memory is insufficient, **data is spilled to disk instead of recomputing** (depending on the storage level).
- Uses more resources for tracking

**📌 Use `cache()` when you're sure the dataset fits in memory.**  
📌 Use `persist()` when working with large datasets or memory-constrained environments.**