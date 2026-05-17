---
title: Snowflake - Streams
tags:
  - snowflake
---
A _stream_ object records the delta of change data capture (CDC) information for a table (such as a staging table), including inserts and other data manipulation language (DML) changes. A stream allows querying and consuming a set of changes to a table, at the row level, between two transactional points of time.

In a continuous data pipeline, table streams record when staging tables and any downstream tables are populated with data from business applications using continuous data loading and are ready for further processing using SQL statements.

It can combine with [[Snowflake - Task]] for some fine control of logics (e.g. slow change dimension)

