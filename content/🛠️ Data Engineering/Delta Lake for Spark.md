---
title: 
tags:
  - spark
---
**Delta Lake** is an open-source storage layer for [[Spark]] that enables relational database capabilities for batch and streaming data. 

**Delta tables** are schema abstractions over data files that are stored in Delta format. For each table, the lakehouse stores a folder containing _Parquet_ data files and a **_delta_Log** folder in which transaction details are logged in JSON format.

The benefits of using Delta tables include:

- **Relational tables that support querying and data modification**. With Apache Spark, you can store data in Delta tables that support _CRUD_ (create, read, update, and delete) operations. In other words, you can _select_, _insert_, _update_, and _delete_ rows of data in the same way you would in a relational database system.
- **Support for _ACID_ transactions**. Relational databases are designed to support transactional data modifications that provide _atomicity_ (transactions complete as a single unit of work), _consistency_ (transactions leave the database in a consistent state), _isolation_ (in-process transactions can't interfere with one another), and _durability_ (when a transaction completes, the changes it made are persisted). Delta Lake brings this same transactional support to Spark by implementing a transaction log and enforcing serializable isolation for concurrent operations.
- **Data versioning and _time travel_**. Because all transactions are logged in the transaction log, you can track multiple versions of each table row and even use the _time travel_ feature to retrieve a previous version of a row in a query.
- **Support for batch and streaming data**. While most relational databases include tables that store static data, Spark includes native support for streaming data through the Spark Structured Streaming API. Delta Lake tables can be used as both _sinks_ (destinations) and _sources_ for streaming data.
- **Standard formats and interoperability**. The underlying data for Delta tables is stored in Parquet format, which is commonly used in data lake ingestion pipelines. Additionally, you can use the SQL analytics endpoint for the Microsoft Fabric lakehouse to query Delta tables in SQL.


See how to:
- [[Create delta tables]]
- [[Work with delta tables in Spark]]
- [[Use delta tables with streaming data]]

