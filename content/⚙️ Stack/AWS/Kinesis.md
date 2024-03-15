# Kinesis

**Kinesis data stream**

- real time streaming service, huge scale ingestion of data from many source
- public service & HA by design
- **default 24-hrs moving window data retention** before processing (can be increased to max. of 365 day), which can be accessed by multiple consumers
- multiple shard store data = stream in parallel
- for data ingestion, analytics, monitoring, app clicks

[[Kinesis/Untitled.png]]

**Kinesis data firehose**

- itself kinesis doesn’t persist data
- full managed service to deliver data to data lakes, data stores and analytic services
- automatic scaling, fully serverless and resilient
- **near** real time delivery (~60s)
- supports transformation of data on the fly with Lambda
- billing the volume

[[Kinesis/Untitled 1.png]]

**Kinesis data analytics**

- real time processing of data using SQL
- ingests from kinesis data streams or firehose
- to destinations (firehose, S3, redshift, elasticsearch & splunk, Lambda, data streams)
- input stream contains data that keeps updating, query by SQL, and go to output stream
- use-case
    - streaming data needing real-time SQL
    - time-series analytic
    - real-time dashboards/ metrics

[[Kinesis/Untitled 2.png]]

**Kinesis video streams**

- ingest live video data from producers
- consumers can access data **frame-by-frame**
- can persist & encrypt
- **can’t access directly via storage, only via API**
- integrate with other AWS services (eg Rekognition & Connect), e.g.:

[[Kinesis/Untitled 3.png]]
