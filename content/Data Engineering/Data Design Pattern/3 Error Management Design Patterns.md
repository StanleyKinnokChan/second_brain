---
title: 3 Error Management Design Patterns
tags:
  - data-engineering
---
Transient errors are often temporary and will eventually recover automatically in the future. The examples could be application overload and unstable network. 

Nontransient errors are not temporary and will never recover by themselves. One example is unprocessable records, also known as poison pill messages. They are fatal issues that stop the application and require your manual intervention.

Maintaining fail-fast approach won’t always be possible, especially for long-running streaming jobs. So error handling is needed. 


p61
**Dead-Letter for Unprocessable Records**:
- save the bad records elsewhere for further investigation
- identifying places in the code where your job can fail, add some safety controls over the likely fail spots that have been identified and save them seperately
- the most common safety control will be a `try-catch`/ `if-else` block
- include the failed message as the metadata to help you better understand the failure at the post-analysis stage
- considerations:
	- resiliency, robust enough to safely hold failures without becoming another failure point.
	- Monitoring and alterting
	- writing performance: the extra time used for the dead-letter queue
	- Allow the replay the pipeline that ingests the failed records into main data flow
	- "Snowball backfilling": the consumer may only recieve part of the data, then replaying the pipeline requries the consumer to take process these records as well
	- distinguish the DL data that is replayed (e.g. add was_dead_lettered flag)
	- can mess up the row order when replay/ the consistency when delivery the data out of the consumer window



**Windowed Deduplicator for Duplicated Records**
![[window deduplicator.png]]
1. identifying the deduplication attributes that guarantee the uniqueness of each record.
2. define the deduplication scope
- batch job:
	- current processed data set for batch job
	- either use distinct/ window function row_number() because they have the full dataset available
- streaming:
	- Data comes continuously and potentially without an end
	- time-based window
	- You can’t look at the entire dataset at once, so you need to remember (keep _state_) what has already been processed
	- This “memory” is kept in a **state store** (e.g. RocksDB in Kafka Streams, in-memory tables in Flink, etc.)
	- Handle out-of-order or late-arriving data
	- put a watermark on top of the event time
		1. it defines the late data arrival boundary
		2. watermark in the deduplication context also controls how long the job remembers the given key

Late Data Detector (mostly for streaming)
1. defining one time-based attribute to track late data => event time (not processing time)
2. define a latency aggregation strategy that will apply individually to each partition in your input data store
	- **min** function: 
		- take the slowest latest time among the partitions to ensure no partitions is left behind to protect compleness. so no "late". But system will have to buffers more. 
		- Completeness-critical pipelines (finance, auditing, ETL)
		- don't use in unbounded streaming as it will stuck at past
		- use in window, batch, state with TTL
	- **max** function: 
		- advance system's clock as quickly as possible and don't wait for slow partition. 
		- RIsk missing/ skipping late events from slower partitions
		- Low-latency, high-throughput pipelines (dashboards, streaming analytics)
	- **hybrid**: 
		- is possible only if you interact with multiple partitioned data sources
		- one aggregation on each source, another aggregation on all source
		- e.g min each source, and max all source
		- balance between latency & performance
3. create/ update watermark (substrate a buffer from the global clock time so that early data that arrives late to be considered as on times) by MAX(event time) - allowed lateness. it has to be monotonic increase


Static Late Data Integrator

Dynamic Late Data Integrator


Filter Interceptor
- when you have multiple filters across different steps, the db will push all the filters of different steps from the start for optimization
- sometimes when you want to troubleshoot, or confirm if the data is reduced due to the filter or software regression, the execution plan won't help
- What we have do is to count the filtered data from the whole data frame for each filtering conditions
- in sql it could be like sum(CASE WHEN a IS NOT NULL THEN 1 ELSE 0 END) AS a_is_not_null, the aggregated table could be saved as a seperate transient/ temp table
- risk: runtime impact, turning stateless job into a stateful one and define boundiary in stream job



Checkpointer for streaming fault tolerance
- the streaming data is often stored in a append-only log. you can’t simply restart them as batch
pipelines since the dataset doesn’t have any particular organizational structure, such as partitions, that could help you figure out what to process next.
- To avoid reprocessing past data, your job must keep track of the most recent
position in the consumed data source, as well as the computed state. The Checkpointer pattern implements this tracking mechanism
- Checkpointing consists of recording the data processing process in a more
persistent storage than the job’s environment, which may change when you restart it.
- two approaches:
	1.  Data processing framework based
		- configuration driven, where you only configure the checkpointing frequency and delegate the execution to your library
		- progress information may be recorded in the environment managed by the framework itself.
		- e.g. [[Spark]] and flink store the progress metadata in a resilient object store with full progress tracking management.

	2. Data store based
		- relies on an intentional checkpointing action from your code
		- interacting with the data store layer for the checkpoint information.
		- e.g. use kafka SDK to kafka topic or AWS KCL to writes checkpoints to [[DynamoDB]] table
- consequences:
	- latency for dealing with metadata and sessions
	- checkpointer != delivery exactly-once. In a distributed system, a task failing **midway**, before a **checkpoint** is recorded can lead to reprocess the data that has been processed by other task -> idempotency is needed