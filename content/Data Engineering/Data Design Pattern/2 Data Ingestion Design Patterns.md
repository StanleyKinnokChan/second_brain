---
title: 2 Data Ingestion Design Patterns
tags:
  - data-engineering
---
Full Load
- considerations:
	- consistency - loss of old data
	- volume

Incremental Load
- strategy
	1. Delta column implementation
	2. partition-based implementation
- consideration:
	- hard vs soft deletes
	- backfilling

Change Data Capture
- Overcome latency problem
- may need to set up with system log
- Complexiy
- alway treat it as dynamic instad of static

Passthrough Replicator
- the api may not be idempotent with the same payload
- should avoid replying on the JSON I/O and use a raw text api to avoid the prior interpretation
- between prod and other env, use push instead of pull strategy
	- - **Control**: Production controls when and how much data is sent.
	- **Safety**: Dev/staging cannot accidentally harm production.    
	- **Consistency**: All target environments get the same snapshot.
- be carefull of PII data before replication
- Don't forget the metadata (e.g. log table in delta lake, header in Kafka)

Transformation Replicator
- Eg when you need to test real data from prod in dev but need to first mask the PII data becuase the compliance rule said that PII data cannot leave prod
- Can be done by custom mapping functions/ select statement to remove the PII column
- Be careful of desynchronization - new PII data come and you need to adapt to it
- Be careful of schema change

Data Compaction
- reduce storage footprint of underlying files. Too many small files can detrimental to process time due to I/O
- e.g. OPTIMIZE in delta lake
- it's a cost and performance trade off
- cleaning up the old file - VACUUM

Data Readiness
- data lake, when another team is the consumer, you cannot directly trigger their workflow but you need a mechanism to flag that the data workflowf is completed
- add an empty "_success" file in each partition folder to indicate that the file loading is completed. 
- It can be then picked up by the consumer (e.g. the file sensor in airflow) = relies on pull semantics
- Considerations
	- late data: need to specify the close of time/ let consumer adapt the old modified data

Event Driven
- producer is in charge of notifying consumers about data availability
- favors push semantics, but still can be pulling where the application constantly listening to the channel (not optimized)
- consumer subscribe to a noti channel, the handler of the application reaction with the event that is fired from the source
- Consideration: 
	- For monitoring, you need to enrich the data by version, processing time, event time, what noti envelop...
	- error handling: Dead-letter pattern