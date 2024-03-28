---
title: 
tags:
  - spark
---
**Through what?**
Spark includes native support for streaming data through **_Spark Structured Streaming_**, an API that is based on a boundless dataframe in which streaming data is captured for processing. 

**Source**
You can use a delta table as a sink or a source for **Spark Structured Streaming**. 
- When being a sink, its dataframe can read data from many different kinds of streaming source, including network ports, real time message brokering services such as Azure Event Hubs or Kafka, or file system locations.
-  When being a source, it enables you to constantly report new data as it is added to the table.

### Using a delta table as a streaming sink
In the following PySpark example, a stream of data is read from JSON files in a folder. The JSON data in each file contains the status for an IoT device in the format `{"device":"Dev1","status":"ok"}` 
New data is added to the stream whenever a file is added to the folder.
```
from pyspark.sql.types import *
from pyspark.sql.functions import *

# Create a stream that reads JSON data from a folder
inputPath = 'Files/streamingdata/'
jsonSchema = StructType([
    StructField("device", StringType(), False),
    StructField("status", StringType(), False)
])
stream_df = spark.readStream.schema(jsonSchema).option("maxFilesPerTrigger", 1).json(inputPath)

# Write the stream to a delta table
table_path = 'Files/delta/devicetable'
checkpoint_path = 'Files/delta/checkpoint'
delta_stream = stream_df.writeStream.format("delta").option("checkpointLocation", checkpoint_path).start(table_path)
```

### Using a delta table as a streaming source
A stream is created that reads data from the table folder as new data is appended. After that you can use the Spark Structured Streaming API to process it.
```
from pyspark.sql.types import *
from pyspark.sql.functions import *

# Load a streaming dataframe from the Delta Table
stream_df = spark.readStream.format("delta") \
    .option("ignoreChanges", "true") \
    .load("Files/delta/internetorders")

# Now you can process the streaming data in the dataframe
# for example, show it:
stream_df.show()
```

### Create Catalog table from stream and query the data
After the streaming process has started, you can query the Delta Lake table to which the streaming output is being written to see the latest data
```
%%sql

CREATE TABLE DeviceTable
USING DELTA
LOCATION 'Files/delta/devicetable';

SELECT device, status
FROM DeviceTable;
```

### Stop the stream
To stop the stream of data being written to the Delta Lake table, you can use the `stop` method of the streaming query:
```
delta_stream.stop()
```