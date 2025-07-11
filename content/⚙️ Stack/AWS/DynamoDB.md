# DynamoDB

**Overview:**

- **NoSQL** **public database-as-a-service** (DBaaS) - **key/value** & **document (not suit for RDB)**
- **no self-managed** servers or infrastructure
- **manual/ automatic** provisioned performance IN/OUT or **on-demand**
- highly resilient.across **AZs** and optionally **global**
- data are replicated to multiple nodes by default
- really **fast - single-digit milliseconds** (SSD based)
- backup, point-in-time recovery, encryption at rest
- support event-driven integration, do things when data change
- **don’t support true SQL**
- access via console, CLI, API
- billed based RCU, WCU, storage & feature
    - i.e. capacity, storage, operation)

Use case:
- when data is hot and smaller, with high I/O
	- eg sensor data, logs, web session, gaming
- big but not frequent-> S3 as data lake
- Traditional transaction/ structured db -> RDS

Primary Key:
- Option 1: Partition Key (HASH)
	- Partition key must be unique for each item
	- Partition key must be “diverse” so that the data is distributed
	- Example: “User_ID” for a users table
- Option 2: Partition Key + Sort Key (HASH + RANGE)
	- The combination must be unique for each item
	- Data is grouped by partition key
	- Example: users-games table, “User_ID” for Partition Key and “Game_ID” for


**Read/ write Capacity:**
- Provisioned mode
	- specify number of reads/ writes per second
	- need to plan capacity beforehand
	- Pay for provisioned read & write capacity units
- On-Demand mode
	- automatically scale up/down with your workloads
	- Pay for what you use, quite expensive (2x-3x more expensive )

**Write Capacity calculation:**
items per second * item size
e.g. 120 item per minutes with item size 2KB = 4 WCU (be careful of WCU)
e.g. 6 item per minutes with item size 4.5 KB = 30 WCU (size must rounded up)

Read mode:
- strongly consistent read
	- If we read just after a write, it’s possible we’ll get some stale data because of replication
- Eventually Consistent Read
	- If we read just after a write, we will get the correct data
	- Set “ConsistentRead” parameter to True in API calls
	- **Consumes twice the RCU**

**Read Capacity calculation:**
RCU repsentes 1 strongly consistent read, or 2 eventually consistent read
If the items are larger than 4KB, more RCUs are consumed and item size must rounded up to 4 multiplier
10 item per second with item size 4KB (strongly consistent)= 10* 4/4 RCU = 10 RCU
16 item per second with item size 12KB (Eventually Consistent)= 16/2 * 12/4 RCU = 24 RCU
10 item per second with item size 6KB (strongly Consistent)= 10 * 8/4 RCU = 24 RCU


Partitions:
- dynamoDB store data in partitions, 
- WCU/ RCU will evenly distributed to each partition
- If hot key/ hot partition is hitting the provisioned ECUs/WCUs, with error:
  "ProvisionedThroughputExceededException", throttling is needed
- Solutions:
	- Exponential backoff from SDK = "error handling strategy for network applications in which a client periodically retries a failed request with increasing delays between requests"
	- Distributed partition keys as much as possible
	- use DynamoDB accelerator (DAX) for RCU problem

API - write
- PutItem:
	- creates a new item or fully replace an old item (same Primary key)
	- Consumes WCUs
- UpdateItem::
	- Edits an existing item’s attributes or adds a new item if it doesn’t exist
	- Can be used to implement A**tomic Counters** – a numeric attribute that’s unconditionally incremented
- Conditional Writes
	- Accept a write/update/delete only if conditions are met, otherwise returns an error
	- Helps with concurrent access to items
	- No performance impact

API - read (get 1 item)
- GetItem
	- Read based on Primary key
	- Primary Key can be HASH or HASH+RANGE
	- Eventually Consistent Read (default)
	- Option to use Strongly Consistent Reads (more RCU - might take longer)
	- ProjectionExpression can be specified to retrieve only certain attributes

API - read (query; for specifc partition key)
**Query returns items based on:**
- **KeyConditionExpression**
    - Must specify **Partition Key** (required; must use `=` operator)
    - May include **Sort Key** (optional; supports `=`, `<`, `<=`, `>`, `>=`, `BETWEEN`, `BEGINS_WITH`)
- **FilterExpression** (optional)
    - Applies **additional filtering** after the query operation (before results are returned)
    - Can **only use non-key attributes** (i.e., not HASH or RANGE keys)
Returns
- Number of items specified in limit, or up to 1MB of data
- pagination is allowed
- can query table, add local secondary index/ global secondary index

API - read (Scan)
- Scan the entire table and then filter out data (inefficient)
- Returns up to 1 MB of data – use pagination to keep on reading
- Consumes a lot of RCU
- Limit impact using Limit or reduce the size of the result and pause
- For faster performance, use Parallel Scan
	- Multiple workers scan multiple data segments at the same time
	- Increases the throughput and RCU consumed
	- Limit the impact of parallel scans just like you would for Scans
- Can use ProjectionExpression & FilterExpression (no changes to RCU)

API - Delete
- DeleteItem - Delete an individual item (conditinoal optional)
- DeleteTable - Delete a whole table and all its items

API - Batch Operations
- Allows you to save in latency by reducing the number of API calls
- Operations are done in parallel for better efficiency
- art of a batch can fail; in which case we need to try again for the failed items
- BatchWriteItem
	- Up to 25 PutItem and/or DeleteItem in one call
	- Up to 16 MB of data written, up to 400 KB of data per item
	- Can’t update items (use UpdateItem)
	- **UnprocessedItems** for failed write operations (exponential backoff or add WCU)
- BatchGetItem
	- Return items from one or more tables
	- Up to 100 items, up to 16 MB of data
	- Items are retrieved in parallel to minimize latency
	- **UnprocessedKeys** for failed read operations (exponential backoff or add RCU)

PartiQL
- SQL-compatible query language for DynamoDB
- Allows you to select, insert, update, and delete data in DynamoDB using SQL, (no join/ agg)
- Run queries across multiple DynamoDB tables
- Run PartiQL queries from
	- AWS Management Console
	- NoSQL Workbench for DynamoDB
	- DynamoDB APIs
	- AWS CLI
	- AWS SDK

Local Secondary Index (LSI)
- Alternative Sort Key for your table (same Partition Key as that of base table)
- Up to 5 Local Secondary Indexes per table
- Must be defined at table creation time
- Attribute Projections – can contain some or all the attributes of the base table
(KEYS_ONLY, INCLUDE, ALL)

Global Secondary Index (GSI)
- Alternative Primary Key (HASH or HASH+RANGE) from the base table
- Speed up queries on non-key attributes
- Attribute Projections – some or all the attributes of the base table (KEYS_ONLY, INCLUDE, ALL)
- Must provision RCUs & WCUs for the index
- Can be added/modified after table creation

Indexes and Throttling
Global Secondary Index (GSI):
- If the writes are throttled on the GSI, then the main table will be throttled, Even if the WCU on the main tables are fine!
- Choose your GSI partition key and Assign your WCU capacity carefully
Local Secondary Index (LSI):
- Uses the WCUs and RCUs of the main table
- No special throttling considerations


DynamoDB Streams
- Ordered stream of item-level modifications (create/update/delete) in a table
- Stream records can be:
	- Sent to Kinesis Data Streams
	- Read by AWS Lambda
	- Read by Kinesis Client Library applications
- Data Retention for up to 24 hours
- Use cases:
	- react to changes in real-time (welcome email to users)
	- Analytics
	- Insert into derivative tables
	- Insert into OpenSearch Service
	- Implement cross-region replication


Time To Live (TTL)
- Automatically delete items after an expiry timestamp
- Doesn’t consume any WCUs (i.e., no extra cost)
- The TTL attribute must be a “Number” data type with “Unix Epoch timestamp” value
- A delete operation for each expired item enters the
- Use cases: reduce stored data by keeping only current items, adhere to regulatory obligation...