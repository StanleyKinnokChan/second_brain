# Aurora

**Architecture & advantage over normal RDS**

[[Aurora/Untitled.png]]

- uses a “cluster”
    - made up of single primary instance ≥ 0 replicas
- no local storage but use cluster volume (share to all computer within cluster)
    - fast provisioning, fast performance, high availability
    - SSD based with 6 replicas across AZs (high IOPS & low latency)
    - replication on storage level, no resource of instance is consumed
- have up to 15 replicas that you can choose failover to
- replicas can be added and removed without requiring storage provisioning
- cluster endpoint point to primary, while reader endpoint point to read replicas with a load-balancer
- can restore by create a new cluster, but **backtrack** can be used which allow in-place rewinds to a previous point in time
- fast clones make a new database much faster than copy all the data
    - only store changes between the source and clone

**Serverless**

- no admin overhead
- don’t need to provision resource
- scalable - ACU - aurora capacity units, which would be adjusted based on load
    - can go to 0 and be paused
    - consumption billing per-second basis
    - same resilience as Aurora (6 copies across AZs)

    [[Aurora/Untitled 1.png]]

    - The overall architecture is similar to Aurora provision, but the ACU will be allocated to customers based on needs
    - client connect to Aurora via proxy fleet managed by AWS
- use case:
    - infrequently used/ new applications (low admin work)
    - variable/unpredictable workloads (scalability)
    - dev/ test databases (can be paused automatically without charging)
    - multi-tenant application of your business (scalability; no “unused” space)

**Global database**

[[Aurora/Untitled 2.png]]

- introduce concept of secondary region (also have 16 replicas, which can promoted to R/W when disaster occurs)
- read replicas will be created from cluster volume
- cross-region DR and business continuity (BE)
- global read scaling with low latency performance
- ~1s replication between regions
- no impact on DB performance

**Multi-master**

- all instances are R/W, no load balancer/ read endpoint
- data committed to the shared storage, propagate to other instance for memory cache
- immediate recover time (default tolerant)
