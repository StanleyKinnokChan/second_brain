---
title: 
tags:
  - Snowflake
---
A materialized view is a pre-computed data set derived from a query specification (the SELECT in the view definition) and stored for later use.
Materialized views are automatically and transparently maintained by Snowflake. Data accessed through materialized views is always current. 

**Use when matching all criteria:**
- The query results from the view don’t change often.
- The results of the view are used often
- The query consumes a lot of resources (expensive aggregates/ simi-structure parsing)


Limitation:
- Can only query a single table
- Cannot query
	- other views
	- Hybrid/ Dynamic tables
	- UDTF
- Cannot include:
	- Joins
	- UDFs
	- window functions
	- having
	- order by
	- limit
	- GROUP BY keys that are not within the SELECT list
	- GROPU BY (GROUPING SETS/ ROLLUP/ CUBE)
	- set operators



https://docs.snowflake.com/en/user-guide/views-materialized