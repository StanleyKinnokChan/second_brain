---
title: 
tags:
---
There are three main (relational) database workloads:
1. As a place to store business transactions as they occur (OLTP)
2. As a place to hold data for complex analysis (OLAP)
3. As a centralized repository for data from different sources (data warehouse)

### 1. OLTP - Online Transaction Processing
- Most business applications require a place to store and retrieve data (a production system)
- As business transactions occur, they are recorded to the database
- Existing rows can be updated
- Data can be retrieved by SQL queries
- Optimized for general use

Traits of OLTP
- Database normalization
- Schema heavily enforced, data integrity
- Strong consistency
- Heavy writes, moderate reads
- Updateable
- Data size MBs to TBs

### 2. OLAP - Online Analytical Processing
- Data stored in a transactional database was not designed for complex analysis
- Data stored in a transactional database can change at any time
- Running complex reports can slow down a transactional database
- Can take time to prepare the data for analysis
- Cubes, dimensions, measures
- optimized for operations like sort, filter, group, join.... without slowing down the DB

Traits of OLAP
- No locking (design for reading, static state when multiple people read it)
- No updates
- Heavy reads, read-only
- Multi-dimensional indexing
- Data size GBs
### 3. Data Warehousing
- Central repository of data from one or more different sources
- Current and historical data used for reporting and analysis
-  Can rename or reformat columns to make it easier for users to create reports
- Users can run reports without affecting the day-to-day business data systems

When to Use a DW
- When queries are long running or affect day-to-day operations
- When data needs further processing (ETL or ELT) before it can be analyzed
- When you want to remove historical data from your day-to-day systems (archiving) 
- When you need to integrate data from several sources
- When users are confused by the data structures, table names or column names 
- When building reports in BI tool

ref:
https://www.stitchdata.com/resources/oltp-vs-olap/