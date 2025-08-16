---
title: 
tags:
  - Snowflake
---
### Snowpipe (Files)

Snowpipe loads data from files as soon as they are available in a stage. The data is loaded according to the COPY statement defined in a referenced pipe.
#### Common Workflow
To enable automatic data ingestion from a stage to Snowpipe, a managed event queue (e.g., AWS SQS) is created when the Snowpipe is set up. You can retrieve the queue's ARN using the `SHOW PIPES` command. This ARN is then configured as the destination for object creation events in the storage service (e.g., S3 event notifications). When a new file is uploaded to the storage (set as external stage), an event is sent to the SQS queue, triggering the execution of the `COPY INTO` statement.

----
##### Two mechanisms:

**Automating Snowpipe using cloud messaging**
- leverage event notifications for cloud storage to inform Snowpipe of the arrival of new data files to load. 
- Snowpipe polls the event notifications from a queue

**Calling Snowpipe REST endpoints**
- calls a public REST endpoint with the name of a pipe object and a list of data filenames.
- POST: provide the file path in the request body, receiving the load status response
- GET: Retrieve the loading history

----
### Snowpipe Streaming (Rows)
- continuous, low-latency loading of streaming data directly into Snowflake. It enables near real-time data ingestion and analysis, crucial for timely insights and immediate operational responses

|Feature / Aspect|Snowpipe Streaming – High-Performance (Preview)|Snowpipe Streaming – Classic|
|---|---|---|
|**SDK**|New `snowpipe-streaming` SDK|`snowflake-ingest-java` SDK (up to v4.x)|
|**Data Flow Management**|Uses **PIPE object** to manage data flow and enable lightweight transformations at ingest time; channels open against the PIPE|No PIPE object; channels are opened directly against target tables|
|**Ingestion Method**|REST API for direct, lightweight ingestion through PIPE|SDK-based ingestion directly into tables|
|**Schema Validation**|Server-side during ingestion, validated against PIPE schema|Typically handled client-side or at query time|
|**Performance**|Significantly higher throughput; improved query efficiency on ingested data|Reliable, but lower throughput compared to high-performance version|
|**Pricing Model**|Transparent, throughput-based pricing (credits per uncompressed GB)|Based on serverless compute usage + number of active client connections|
|**Use Case**|Recommended for new streaming projects needing high throughput, predictable cost, and advanced capabilities|Reliable solution for established pipelines, production-ready but less performant|

**offset token:**
- like a bookmark/ resume point for your data, tracking how far you’ve ingested data into Snowflake so you know which rows have already been processed.
- When you send data to Snowpipe Streaming (via `insertRow/insertRows` or `appendRow/appendRows`), you include an **offset token** for each row or batch. Snowflake stores this token after the data is successfully committed. Later, you can ask Snowflake for the **latest committed offset token** to see how far ingestion has progressed.

---
#### Checking

Check pipe status by `PIPE_STATUS`
```
SYSTEM$PIPE_STATUS( '<pipe_name>' )
```

Retrieve details about all loading activity in a table using `COPY_HISTORY`
```
select *
from table(information_schema.copy_history(TABLE_NAME=>'MYTABLE', START_TIME=> DATEADD(hours, -1, CURRENT_TIMESTAMP())));
```

Retrieve error in a past execution of the COPY INTO command and returns all the errors encountered during the load using `VALIDATE`
```
SELECT * FROM TABLE(VALIDATE(t1, JOB_ID=>'5415fa1e-59c9-4dda-b652-533de02fdcf1'));
```

Retrieve error for any loads for the `mypipe` pipe within the previous hour using `VALIDATE_PIPE_LOAD`:
```
select * from table(validate_pipe_load(
  pipe_name=>'MY_DB.PUBLIC.MYPIPE',
  start_time=>dateadd(hour, -1, current_timestamp())));
```

