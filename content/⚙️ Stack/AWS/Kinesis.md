# Kinesis

##### **Kinesis data stream**

- real time streaming service, huge scale ingestion of data from many source
- public service & HA by design
- **default 24-hrs moving window data retention** before processing (can be increased to max. of 365 day), which can be accessed by multiple consumers
- multiple shard store data = stream in parallel
- for data ingestion, analytics, monitoring, app clicks
- records size limit is that: input - 1mb/s per shard and; output - 2mb/s per shard
#### Producer
**Kinesis producer SDK - Putrecords**
- APIs that are used are Putrecord(s), which uses batching and increase throughput, so less HTTP requests
- ProvisionedThroughputExceeded if we go over limits
	- make sure you don't have a hot shard -> choose a partition key
	- retries with backoff
	- increase shards
- Usecase: low throughput, high latency, simple API
- managed AWS sources used this under the hood
	- AWS IoT
	- CloudWatch Logs
	- Kinesis Data Analytics
**Kinesis Producer Library (KPL)**
- C++/Java library
- Usecase: high performance, long-running producers
- automated and configurable retry mechanism
- Synchronous or Asynchronous API (better performance but hv to deal with the synchronizing issue)
- Allow summiting metrics to cloudwatch
- Batching by default - increase throughput, decrease cost:
	- Collect: "Gather individual data records and send them out in single API call", records and write to multiple shards in the same PutRecords API call. 
	- Aggregate: "Combine multiple small records into one big record." increased latency
- Compress must be implemented by the user
- KPL records must be de-coded with KCL or special helper library
- When not to use
	- when the application cannot tolerate the delay caused by RecordMaxBufferedTime => use SDK putrecords instead
**Kinesis Agent**
- monitor log files and sends them to kinesis data streams
- built on top of kpl, installed in linux-based server env
- features:
	- write from multiple directories and write to multiple streams
	- routing feature based on directory/ log file
	- pre-process data before sending to streams (csv to json, log to json...)
	- handles file rotation, checkpointing, and retry upon failures
	- emits metrics to cloudwatch for monitoring

#### Consumer
- Kinesis SDK
- Kinesis Client library (KCL)
- Kinesis Connector Library
- 3rd party: spark, kafka, Flume....
- AWS lambsda
- Kinesis Firehose
- Kinesis Data analytics
**Kinesis SDK**
- records are polled by consumers from a shard withing a GetRecord()
- GetRecords return up to 10 MB of data/ 1000 records
- max of 5 GetRecords API calls per shard per second (more consumer, less througthput)
**Kinesis Client Library (KCL)**
- read recods from kinesis produced with the kpl
- share multiple shards with multiple consumers in a "group"
- checkpointing feature to resume progress (if service go down)
- use dynamoDB for coordination and checkpointing (one row per shard)
- ExpiredIteratorException => increase WCU
**Kinesis Connector library**
- leverages KCL library
- Must run on EC2
- write data to: S3/ DynamoDB/ Redshift/ Opensearch
- kidda replaced by lambda and firehost
**Lambda**
- has a library to de-aggregate record from KPL
- can be used to trigger noti in real time
- has a configurable batch size

##### **Consumers Options**
**Standard consumers:**
- low number of consuming application (1,2,3..)
- can tolerate ~200 ms latency
- minimize cost
**Enhanced Fanout**
- The consumer subscribes the shard and let data streams push the data to consumer
- 2MB/s per shard PER CUSTOMER!! (no more 2MB/s limit)
- reduce latency (to ~70 ms)
- default limit of 20 consumers
- higher costs

**Kinesis Operations**
- Adding shards (aka shard splitting): behind the hood, old one is deleted once data is expired  and two new one are added
- Merging shards to save cost: two new one are deleted once data is expired and add a new old
- These operation could casue out-of-order records (consumers switch to read the data from the new child shards and left the old data in the parent) -> make sure you need to consume all data from parents first (KCL already built in )
- re-sharding cannot be done in parallel, plan capacity in advance and it take time

**Handling Duplicates**
- producer retires (send same data) due to network timeouts (before data stream reply) 
	- fix: embed unique record ID in the data to de-dup on the consumer side
- Consumer retries (read same data) due to:
	- worker terminiates unexpectedly
	- workerinsteances are added or removed
	- shards are merged or split
	- application is deployed
- Fixed:
	- make sure application idempotent
	- handle de-dup in the final des

Troubleshooting:
Producer
- Write is too slow
	- hit the service limit/ shard-level limit and being throttled
	- hot shard
- large producers
	- batch things up, use KPL with collect/ agg
- 500/503 error (error rate>1%)
	- implement retry mechanism
- connection erros from flink to kinesis
	- network issue/ lack of resources in Flink's env
	- VPC misconfigured
- timeout from flink to kinesis
	- increase timeout
- Throttling error
	- random partition key
	- exponential backoff
	- rate-limit
Consumer
- records get skipped with KCL
	- check for unhandled exceptions on processRecods
- Records in same shard are processed by more than 1 processor
	- may be due t failover on the record processor workers (aka >1 per shard)
	- handle the zombie processor
- read too slow
	- increase number of shards
	- maxRecords per call is too low
- Shard Iterator expires unexpectedly
	- may need more write capacity on the shard table in DynamoDB
- record processing failling behind
	- increase retention period and increase resource
- Lambda function can't get invoked
	- permissions issue on execution role
	- function is timing out (check max execution time)
	- breaching concurrency limit
- ReadProvisionedThroughputExceeded exception
	- throtting
	- reshard
	- reduce size of get records requests
	- use enhanced fan-out
	- use retires and exponential backoff
- High latency
	- monitor with GetRecords
	- increase shards
	- increase retention period
##### **Kinesis Data Firehose (KDF)**

- store data into final des in batch (data sink like redshift/ S3/ OpenSearch), the source record to S3 as well
- itself kinesis doesn’t persist data, it cumulates in a buffer and flushed based on time and size
	- buffer size (ex: 32 MB): will be hit for high throughput
	- buffer time (ex: 2min): will be hit for low throughput
- in-flight transform data with lambda functions/ support format conversion/ compression
- full managed service to deliver data to data lakes, data stores and analytic services
- automatic scaling, fully serverless and resilient
- **near** real time delivery (~60s)
- supports transformation of data on the fly with Lambda
- billing the volume
- Spark/ KCL do not read from KDF, only data stream

##### **Kinesis Data Analytics** (managed service for Apache Flink)

- real time processing of data from stream,using table API for SQL access
- ingests from kinesis data streams or firehose, or reference table from s3
- to destinations (back to firehose/ data streams, S3, redshift, elasticsearch & splunk, post-processing in Lambda)
- input stream contains data that keeps updating, query by SQL, and go to output stream
- connector lbrary llow flink to talk to anything you have an SDK for
- operators allow the transformation from one or more datastream into a new datastream
- FANDOM_CUT_FOREST: a sql function used for anomaly detection (outliers) on numeric columns in a stream
- use-case
    - streaming ELT
    - Continuous metrics generation
    - Responsive/ time-series analytics

#####  **MSK** Managed Streaming for Apache Kafka
- alternative to kinesis
- Fully managed apache kafka
	- allow you to create, update, delete clusters
	- managed brokers nodes and zookeeper
	- data is stored on EBS volumes (1GB - 16 TB)
- build producers and consumers
- create custom configurations for your clusters
	- default message size of 1MB (can set up to 10 MB)
	- broker instance type
	- number of broker per AZ
	- size of EBS volumes
- Managed connect (to send/ recieve the message from/ to MSK)
- 3 ways of Authentication (AuthN) & authorization (AuthZ)
	- Mutual TLS (AuthN) + Kafka ACLs (AuthZ)
	- SASL/SCRAM (AuthN) + Kafka ACLs (AuthZ)
	- IAM Access Control (AuthN + AuthZ)
- Multi-level cloudwatch metrics
	- basic (cluster and borker metrics)
	- Enhanced (enhanced broker metrics)
	- Topic-level (enhanced topic metrics)

![[Pasted image 20250625104421.png]]

#####  **Kinesis video streams**

- ingest live video data from producers
- consumers can access data **frame-by-frame**
- can persist & encrypt
- **can’t access directly via storage, only via API**
- integrate with other AWS services (eg Rekognition & Connect), e.g.:

[[Kinesis/Untitled 3.png]]
