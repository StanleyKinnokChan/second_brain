# RDS - read replicas

[[RDS - read replicas/Untitled.png]]

[[RDS - read replicas/1_Z_c3IDlJObX6y-XQ5C5P0A.webp]]

- advantages
    - performance for read operations
        - 5x direct read- replicas per DB instance
        - each providing an additional instance of read performance
        - read-replicas can created from read-replicas, but lag starts can be a problem
    - able to have cross-region failover capability
    - meet low recovery time objective
- read replicate has its own endpoint address, separate individual from primary
- created with asynchronous replication
- When create cross-region failover, AWS handle all of the networking between regions and fully encrypted in transit

**RPO/RTO improvements**

- snapshots & backups improve RPO = limit the data loss
however, RTO’s are the problem = snapshots take a long time
- Read Replica’s offer near 0 RPO, can be promoted quickly (low RTO)
- recover from **failure only but not data corruption**, the read replica are also corrupted if this happens
- read only until promoted
- global availbility improvements and global resilience
