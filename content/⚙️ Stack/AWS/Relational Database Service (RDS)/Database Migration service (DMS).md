# Database Migration service (DMS)

- runs using a replication instance, each runs multiple replication tasks
- **source** and **destination** endpoints point at **source** and **target databases**
- one endpoint must be on AWS

[[Database Migration service (DMS]]%20966228264d5b47cb852450eaa0b09fd5/Untitled.png)

- CDC captures changes during the migration
- DMS itself didn’t support schema conversion, but can work with schema conversion tool (SCT) to do it

**Schema conversion tool (SCT)**

- the engine has to be different

[[Database Migration service (DMS]]%20966228264d5b47cb852450eaa0b09fd5/Untitled%201.png)

**Work with snowball for more rapid & efficient migration**

[[Database Migration service (DMS]]%20966228264d5b47cb852450eaa0b09fd5/Untitled%202.png)
