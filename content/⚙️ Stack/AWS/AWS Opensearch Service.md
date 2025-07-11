
- Petabyte-scale analytic and reporting
- a search engine but also analytic and reporting
- often along with kinesis for Realtime bigdata
- applications
	- full-text search
	- log analytics
	- application monitoring
	- security analytics
	- clickstream analytics
- 3 entities
	- Documents: text/ structured json, every document has a unique id and type
	- type (depreciate soon): defines schema and mapping shared by documents 
	- indices: the object being searched like a database, included all documents within a collection of types, which split into shard, each of which may be on a different node in a cluster

Characteristics:
- Fully-managed
- scaling without downtime
- pay for what you use
- network isolation
- AWS integration
	- S3 via lambda to kinesis
	- kinesis data streams
	- dynamoDB streams
	- cloudwatch/ cloudtrail
	- zone awareness

Options:
- dedicated master nodes (choice of count and instance types)
- domains: a cluster with all configuration
- snapshots to S3
- zone awareness

Security
- network isolation
- Resource-based policies
- identity- based polices
- IPs-based polices
- request signing
- put cluster into VPC instead of open to public (harder to connect) (have to decide from start)
- use Cognito to get in the dashboard within a VPC from enterprise identity providers like Microsoft active directory using SAMLs

Anti-patterns
- OLTP
- ad-hoc data querying (Athena is better)
- remember OpenSearch is primarily for search and analytics

Storage:
- Hot "standard": instance stores/ EBS volumes, fastest performance
- ultrawarm: use S3 + caching, slower performance but much lower cost (must have dedicated master node)
- cold storage: use S3, even cheaper. (must have dedicated master node and not compatible with T2/ T3 instance types)
- can migrate between storage type

Index State Management
- Automate index management policies
- example
	- delete old indices after period of time
	- move indices into read only after a period of time for compliance purpose
	- move indices between storage type over time
	- reduce replica count over time
	- automate index snapshots
- ISM polices are run every 30-48 minutes 
- can send noti when done
- index rollups
	- can roll up old data into summarized indices for time-series
	- saves storage costs
	- new index may have fewer fields, coarser time buckets
- Index transforms
	- create a different view to analyze data differently
	- reshape data with pivot, stats, group...
	- grouping/ aggregations

Cross-cluster replication
	- replicate indices/ mappings/ metadata across domains
	- ensures high availability in an outage
	- replicate data geographically for better latency
	- Leader - Follower pattern
	- requires frine-grained access control and node-to-node encryption
	- "Remote Reindex" allows copying indices from one cluster to another on demand

Stability
- 3 dedicated master nodes is best to avoids "split brain" ( doesn't know which half is true)
- Make sure not running out of disk space 
- choose a good number of shard, may need to limit the nubmer of shard per node
- choose a instance types
	- at least 3 nodes
	- mostly about storage requirements as OpenSearch is storage heavy

Performance (JVMMemoryPressure error)
- unbalanced shard allocations/ too many shards that pressure memory
- Fewer shards can yield better performance by deleting old/ unused indices