# Redshift

- petabyte-scale **data warehouse**
- OLAP (column based), not OLTP (row based like RDS/ transaction) ⇒ good for aggregated/ analysis
- pay as you use
- direct query S3 using **redshift spectrum** without loading data
- direct query other DBs using **federated query** without loading data
- integrates with AWS tooling such as Quicksight
- SQL-like interface JDBC/ODBC connection
- Redshift does not support table partitioning

**Architecture**

[[Redshift/Untitled.png]]

- **server based** (not **serverless like Athena**)
- 1 AZ in a VPC, not HA by design
- run multiple nodes
    - leader node - query input, planning and aggregation
    - compute nodes - performing queries of data
- can configure VPC security, IAM permissions, KMS at rest encryption, CE monitoring
- can enable **Amazon Redshift enhanced VPC routing** (forces the traffic to go through your VPC but not public network; for customized network)

**DR and Resilience**
- Replication within cluster
- Backup to S3 Asynchronously replicated to another region
- Automated snapshots
- Failed drives / nodes automatically replaced
- However – limited to a single availability zone (AZ)
- Vertical and horizontal scaling on demand


Redshift Spectrum (S3 data shown in redshift as table)
- Query exabytes of unstructured data in S3 without loading into Redshift cluster
- Limitless concurrency
- Horizontal scaling
- Separate storage & compute
- Wide variety of data formats
- Support of Gzip and Snappy

Distribution styles
- AUTO
	- Redshift figures it out based on size of data
- EVEN
	- Rows distributed across slices in round-robin
- KEY
	- Rows distributed based on one column
- ALL
	- Entire table is copied to every node (like the case for boardcast join)

VACUUM command
- VACUUM DELETE ONLY:	Remove deleted rows only (no sorting) (Redshift only do a soft delete)
- VACUUM SORT ONLY: Sort rows without removing deleted rows (keep sort sort order sharp)
- VACUUM FULL	Does both delete cleanup and sorting (default)
- VACUUM REINDEX	Rebuilds interleaved sort keys (keep the index effective from skew), followed by a VACUUM FULL  

System table:
- STL_ALERT_EVENT_LOG records any alerts/notifications related to queries or user-defined performance thresholds. This would capture optimizer alerts about potential performance issues.
- STL_PLAN_INFO provides detailed info on execution plans. The optimizer statistics and warnings provide insight into problematic query plans.
- STL_USAGE_CONTROL limits user activity but does not log anomalies.
- STL_QUERY_METRICS has execution stats but no plan diagnostics.

Importing / Exporting data
- COPY command
	- Parallelized; efficient
	- From S3, EMR, DynamoDB, remote hosts
	- S3 requires a manifest file and IAM role
- UNLOAD command
	- Unload from a table into files in S3
- Enhanced VPC routing
	- force all copy and unload traffic via amazon vpc
- Auto-copy from Amazon S3
- Amazon Aurora zero-ETL integration
	- Auto replication from Aurora -> Redshift
- Redshift Streaming Ingestion
	- From Kinesis Data Streams or MSK

Security
- VPC network isolation
- cluster security groups
- encryption in flight using the JDBC driver enabled with SSL
- encryption at rest using KMS *OR an HSM device (establish a connect)!!!!
- supports S3 SSE using default managed key
- use IAM roles for redshift (load/ dump data to S3/ KMS)

