---
title: 
tags:
  - spark
---
## Using Spark SQL

The most common way to work with data in delta tables in Spark is to use Spark SQL
```
spark.sql("INSERT INTO products VALUES (1, 'Widget', 'Accessories', 2.99)")
```
Alternatively, you can use the `%%sql` magic in a notebook to run SQL statements.
```
%%sql UPDATE products SET Price = 2.49 WHERE ProductId = 1;
```

## Use the Delta API
 work with delta files rather than catalog tables, it may be simpler to use the Delta Lake API
```
from delta.tables import *
from pyspark.sql.functions import *

# Create a DeltaTable object
delta_path = "Files/mytable"
deltaTable = DeltaTable.forPath(spark, delta_path)

# Update the table (reduce price of accessories by 10%)
deltaTable.update(
    condition = "Category == 'Accessories'",
    set = { "Price": "Price * 0.9" })
```
## Use _time travel_ to work with table versioning
Modifications made to delta tables are logged in the transaction log for the table. You can use the logged transactions to view the history of changes made to the table and to retrieve older versions of the data (known as _time travel_)
To see the history of a table, you can use the `DESCRIBE` SQL command as shown here.
```
%%sql DESCRIBE HISTORY products
```

retrieve data from a specific version of the data by specifying the version
```
df = spark.read.format("delta").option("versionAsOf", 0).load(delta_path)
```

OR retrieve data from a specific version of the data by specifying the timestamp
```
df = spark.read.format("delta").option("timestampAsOf", '2022-01-01').load(delta_path)
```