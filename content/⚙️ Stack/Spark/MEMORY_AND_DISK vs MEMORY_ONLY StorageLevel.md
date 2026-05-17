---
title: MEMORY_AND_DISK vs MEMORY_ONLY StorageLevel
tags:
  - spark
  - exam
---
MEMORY_AND_DISK: for when df is too expensive to recompute and doesn't fit into memory, then it better to use this to read from memory first then the disk. 

MEMORY_ONLY: In most cases, this is the better options