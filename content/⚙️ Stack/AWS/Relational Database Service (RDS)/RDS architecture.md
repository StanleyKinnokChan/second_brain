# RDS architecture

[[RDS architecture/Untitled.png]]

- database server as a service (DBSaaS)
- multiple database on one single DB server
- choice of DB engines (MySQL, mariaDB, postgreSQL, Oracle..)
- Amazon aurora is a different product
- **no access to OS/ SSH access**
    - but can be connected using SSH, session manager for MSSQL & oracle via RDS customization
- operate within subnet in a VPC in a region
- **for RDS each instance has its own dedicated EBS-provided storage**
- standbys using synchronous replication across
- backup to S3
- cost
    - instance size & type
    - multi AZ or not (more than 1 instance)
    - storage type & amount (EBS)
    - data transferred (in and out)
    - backups & snapshots
    - licensing if applicable

**Multi AZ - instance mode**

[[RDS architecture/Untitled 1.png]]

- data ⇒ primary and replicated to standby (synchronous)
- not free tier .. extra cost for replica
- 1 standby replica only, which can’t be used for read or writes (just store)
- 60-120s failover
- same region only
- backups taken from standby to improve performance

**Multi AZ - cluster mode**

[[RDS architecture/Untitled 2.png]]

- 1 writer and 2 readers DB instances (high availability)
- much faster hardware
- fast writes to local storage ⇒ flushed to EBS
- readers can be used for reads… allowing some read scaling
- replication is via transaction log…more efficient
- failover is faster ~35s + transaction log apply
- writes are committed when 1 reader has confirmed
