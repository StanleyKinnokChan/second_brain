# Redshift

- petabyte-scale **data warehouse**
- OLAP (column based), not OLTP (row based like RDS/ transaction) ⇒ good for aggregated/ analysis
- pay as you use
- direct query S3 using **redshift spectrum** without loading data
- direct query other DBs using **federated query** without loading data
- integrates with AWS tooling such as Quicksight
- SQL-like interface JDBC/ODBC connection

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

[[Redshift/Untitled 1.png]]

- redshift itself is not HA, but it can achieve HA by the automatic/ manual incremental backups in **same/ cross regions**
