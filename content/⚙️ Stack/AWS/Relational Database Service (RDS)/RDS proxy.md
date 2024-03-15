# RDS proxy

- fully managed DB proxy for RDS/ Aurora
- provides connection pooling
- auto-scaling, highly available by default
- only accessible from a VPC
- accessed via proxy endpoint
- can enforce SSL/TLS
- can reduce failover time by over 60%
- abstracts failure away from you application

**Why exist:**

- opening and closing connection consume resources
- if you need to have many connection each with a little data update, it takes time and create latency + handle failure of database instance during conenction is hard
- application ⇒ proxy (always connect to database) ⇒ database

[[RDS proxy/Untitled.png]]

**Use case:**

- too many connections
- AWS lambda (time saved/ connection reuse)
- long running connections (SAAS apps) for low latency
- reduce the time for failover
