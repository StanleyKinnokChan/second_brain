---
title: 4 Idempotency Design Patterns
tags:
  - data-engineering
---

Overwriting
Fast Metadata Cleaner for partitioned dataset
- The delete operation of a big table could be slow, so store multiple small table with the idempotency granularity (e.g. 1 week) -> use drop/ truncate to remove old data + recreate the small table
- delete operation need to read row, drop/ truncate didn't => metadata

Data Overwrite for object storage
- in sql, insert overwrite into = truncate the table and insert the selected row