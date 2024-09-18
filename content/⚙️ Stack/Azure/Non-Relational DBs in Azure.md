---
title: 
tags:
  - Azure
  - Database
---
[[Cosmos DB]]
- Enterprise-grade non-relational database
- Supports many data models (graph, document, table, column-family)
- Compatible with established APIs (Cassandra, MongoDB, Gremlin, Etcd) for different data storage, but cannot change once selected and no mix-n-match
- Select the data consistency you need
- Easy to scale worldwide
- Sub-10 ms latency
- Service Level Agreements for throughput, latency, availability and consistency

**Table Storage**
- Azure Storage account
- 5 PB maximum limit
- $0.045 per GB - cheapest data storage option on Azure
- Plus pay for operations - $0.00036 per 10,000 transactions
- Service Level Agreement shockingly poor (10 seconds for a query)

**Blob Storage**
- Azure Storage account
- 5 PB maximum limit ● $0.0208 per GB - cheapest data storage option on Azure ● Supports premium, hot, cool, archive access tiers
- Supports “reserved capacity” - ~$0.014 per GB for 100TB/3 years
- Supports blob indexing
- Plus pay for operations - $0.00036 per 10,000 transactions
- Service Level Agreement shockingly poor (2 seconds per MB)

**File Storage**
- Azure Storage account
- 5 PB maximum limit
- $0.06 per GB - cheapest data storage option on Azure
- Standard and premium options
- Service Level Agreement shockingly poor (2 seconds per MB)