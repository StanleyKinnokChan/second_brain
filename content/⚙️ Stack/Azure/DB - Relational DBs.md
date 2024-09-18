---
title: 
tags:
  - Azure
  - Database
---
## Benefits of relational DBs
- Normalization
- Data relationships drive data insights
- Data Integrity
- Many products are decades old, bug free, stand-still over time
- BI tools makes data accessible
- Database enforce constraint, fixed schema

## Azure SQL Family of Products
- **SQL Server in a VM** (IaaS)
	- Managed everything (OS upgrades, backups, replication)
	- no Limitations of storage
	- pay for server & licensing, not per DB
	- image different systems/ versions available in Marketplace
	- different tiers
	- no retooling, just change the connection string
- **SQL Managed Instance** (PaaS)
	- close to 100% compatibility to SQL server on premises
	- fully-managed service
	- 32GB to 8TB storage/ 4 to 80 vCore
	- very few case where the setting is different (e.g. encryption method)
	- less common 
- **Azure SQL Database** (PaaS)
	- close to 100% compatibility to SQL server on premises
	- lots of options for provisioned and serverless data bases
	- pay for performance/ hardware
	- starting at $5 per month
	- choose single DB/ elastic pool, can scale without downtime
	- need additional tool to tune the DB

## Open-Source Database System (MS managed them)
- Azure Database for mySQL, PostgreSQL, MariaDB (useful for migration to MS cloud)
- PostgreSQL for CosmosDB (non-relational to relationship)
- Compatible with your legacy systems