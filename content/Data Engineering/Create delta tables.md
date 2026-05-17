---
title: Create delta tables
tags:
  - data-engineering
  - spark
---
## Creating a delta table (both able schema definition + data files in delta format) directly from a dataframe
One of the easiest ways to create a delta table in [[Spark]] is to save a dataframe in the _delta_ format
```
# Load a file into a dataframe
df = spark.read.load('Files/mydata.csv', format='csv', header=True)

# Save the dataframe as a delta table
df.write.format("delta").saveAsTable("mytable")
```
## _Managed_ vs _external_ tables
**_managed_ table :** meaning that the table definition in the metastore and the underlying data files are both managed by the [[Spark]] runtime for the current lakehouse
```
# creating a managed delta table
df.write.format("delta").saveAsTable("managed_products")
```
**_external_ tables:** the relational table definition in the metastore is mapped to an alternative file storage location
```
# creating a external delta table
# specify a fully qualified path for a storage location
df.write.format("delta").saveAsTable("myexternaltable", path="abfss://my_store_url..../myexternaltable")
```

> [!warning] Ongoing Makeover
> For managed tables, deleting the table **will also** delete the underlying files from the **Tables** storage location for the lakehouse.
> While for external tables, deleting an external table from the lakehouse metastore **does not** delete the associated data files.


## Creating table metadata (without saving any data files)
#### 1. Use the _DeltaTableBuilder_ API
write [[Spark]] code to create a table based on your specifications
```
from delta.tables import *

DeltaTable.create(spark) \
  .tableName("products") \
  .addColumn("Productid", "INT") \
  .addColumn("ProductName", "STRING") \
  .addColumn("Category", "STRING") \
  .addColumn("Price", "FLOAT") \
  .execute()
```
#### 2. Use Spark SQL
use sql create a managed table
```
%%sql

CREATE TABLE salesorders
(
    Orderid INT NOT NULL,
    OrderDate TIMESTAMP NOT NULL,
    CustomerName STRING,
    SalesTotal FLOAT NOT NULL
)
USING DELTA
```
or create an external table by specifying a `LOCATION` parameter
```
%%sql

CREATE TABLE MyExternalTable
USING DELTA
LOCATION 'Files/mydata'
```

## Save data in delta format (without creating a table definition)
 This approach can be useful when you want to persist the results of data transformations performed in [[Spark]] in a file format over which you can later "overlay" a table definition or process directly by using the delta lake API.

saves a dataframe to a new folder location in _delta_ format, where the **data** and a **delta_log** folder were stored:
```
# save to a path instead of using .saveAsTable()
delta_path = "Files/mydatatable"
df.write.format("delta").save(delta_path)
```

Any modifications made to the data through the delta lake API or in an external table that is subsequently created on the folder will be recorded in the transaction logs.

You can replace the contents of an existing folder with the data in a dataframe by using the **overwrite** mode, as shown here:
```
new_df.write.format("delta").mode("overwrite").save(delta_path)
```
You can also add rows from a dataframe to an existing folder by using the **append** mode:
```
new_rows_df.write.format("delta").mode("append").save(delta_path)
```

Next? See [[Work with delta tables in Spark]]