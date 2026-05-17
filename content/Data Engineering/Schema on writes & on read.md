---
title: Schema on writes & on read
tags:
  - data-engineering
---
Schema on write is essentially the traditional data warehouse pattern: a table has an integrated schema; any writes to the table must conform. To support schema on write, a data lake must integrate a schema metastore.

With schema on read, the schema is dynamically created when data is
written, and a reader must determine the schema when reading the data. Ideally, schema on read is implemented using file formats that implement built-in schema information, such as Parquet or JSON. CSV files are notorious for schema inconsistency and are not recommended in this setting.

**Advantage:**
The principal advantage of schema on write is that it enforces data
standards, making data easier to consume and utilize in the future. 

Schema on read emphasizes flexibility, allowing virtually any data to be written. This comes at the cost of greater difficulty consuming data in the future.