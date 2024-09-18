---
title: 
tags:
  - Azure
  - Database
---
Any DB that is not based on tables, rows and columns. The data is stored better supports the application's use. Use NoSQL (not only SQL) to query data

Benefits of non-relational DBs
- Optimized for specific data types
- Can be designed for performance at internet scales
- Might not require massive hardware, reduced expense
- Many of these DBs are Open source

**Type of data**
- document/ Json document
	- use key and document (a Json entity, can be nested)
	- Azure Product: Cosmos DB core SQL
- Column-Family Data
	- use key and column family (a group of columns, the columns of each row can be not fixed)
	- Azure Product: Cosmos DB Cassandra API
- Key-Value
	- use key and hash value (not meant to be searchable, e.g. useful for cache)
	- Azure Product: Cosmos DB Table API
- Graph data
	- nodes and relationship between nodes
	- Azure Product: Cosmos DB graph API
- Time series
	- work around timestamp (e.g. IoT monitor thing every ms)
	- Azure Product: Time Series Insight
- Object data
	- data storage
	- Azure Product: Blob Storage

