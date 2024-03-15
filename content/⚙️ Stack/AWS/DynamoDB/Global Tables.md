# Global Tables

[[Global Tables/DynamoDB_Global-Tables-01.dad2508b80e8b7c544fe1a94a2abd3f770b789da.png]]

<aside>
💡 Global tables replicate your DynamoDB tables automatically across your choice of AWS Regions.

They eliminate the difficult work of replicating data between Regions and resolving update conflicts

</aside>

- provides **multi-master cross-region** replication, all tables can be used for **read & write operation**
- tables are created in multiple regions and added to the same global table (becoming replica tables)
- **last writer wins** is used for conflict resolution
- **reads & writes** can occur to **any region**
- generally **sub-second** replication between regions
- strongly consistent reads **ONLY** in the same region as writes
- provides global HA & global DR/BC
