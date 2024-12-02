# Materialization

DBT wrap the model queries with DDL or DML and create view or table in the Datawarehouse. 

### Ephemeral model:
take the select statement, it imports the statement as CTEs as downstream model and keep the data warehouse clean. However, It cannot be reference and hard to debug
	Use cases:
		-very light-weight transformations that are early on in your DAG
		- are only used in one or two downstream models, and
		- do not need to be queried directly

### Materialized View:
a combination of a view and a table, and serve use cases similar to incremental models, usually able to be refreshed without manual interference on a regular cadence. Not supported by every DB platform and few configuration due to the complexity
	Use cases:
	 - where incremental models are sufficient, but you would like the data platform to manage the incremental logic and refresh.

### Incremental:
use this when we want to append data to tables for fact tables, and won't mess with the historical records. The appending records is specified by a jinja snippet as a WHERE clause.

### View
lightweight 