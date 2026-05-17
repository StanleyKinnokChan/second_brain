---
title: Spark
tags:
  - data-engineering
  - spark
---
Apache Spark is a distributed data processing framework that enables large-scale data analytics by coordinating work across multiple processing nodes in a cluster

You submit a data processing job in the form of some code that initiates a _driver_ program, which uses a cluster management object called the _SparkContext_ to manage the distribution of processing in the Spark cluster.

Spark uses a data structure called a _resilient distributed dataset_ (RDD)


**Example - loading a DF:**
The line at the beginning is called a _magic_, and tells Spark that the language used in this cell is PySpark. You can select the language you want to use as a default in the toolbar of the Notebook interface, and then use a magic to override that choice for a specific cell.
```
%%pyspark
df = spark.read.load('Files/data/products.csv',
    format='csv',
    header=True
)
display(df.limit(10))
```

**Example - Load partitioned data
```
road_bikes_df = spark.read.parquet('Files/bike_data/Category=Road Bikes')
display(road_bikes_df.limit(5))
```

**Example - Specifying an explicit schema:**
specify an explicit schema for the data, which is useful when the column names aren't included in the data file, like this CSV example
```
from pyspark.sql.types import *
from pyspark.sql.functions import *

productSchema = StructType([
    StructField("ProductID", IntegerType()),
    StructField("ProductName", StringType()),
    StructField("Category", StringType()),
    StructField("ListPrice", FloatType())
    ])

df = spark.read.load('Files/data/product-data.csv',
    format='csv',
    schema=productSchema,
    header=False)
display(df.limit(10))
```

**Example - select column:**
```
pricelist_df = df.select("ProductID", "ListPrice")
```

**Example - select and aggregate column:**
```
counts_df = df.select("ProductID", "Category").groupBy("Category").count() display(counts_df)
```

**Example - select and filter column:**
```
bikes_df = df.select("ProductName", "Category", "ListPrice").where((df["Category"]=="Mountain Bikes") | (df["Category"]=="Road Bikes"))
display(bikes_df)
```

**Example - add column:**
```
transformed_df = df.withColumn("Year", year(col("OrderDate"))).withColumn("Month", month(col("OrderDate")))
```

**Example - split column:**
```
transformed_df = transformed_df.withColumn("FirstName", split(col("CustomerName"), " ").getItem(0)).withColumn("LastName", split(col("CustomerName"), " ").getItem(1))
```

**Example - save df:**
```
bikes_df.write.mode("overwrite").parquet('Files/product_data/bikes.parquet')
```


**Example - output as parquet files
Creating a [[2.1 Delta Lake for Spark]] table uses almost identical syntax – it’s as easy as switching your format from "parquet" to "delta":
```
df.write.format("parquet").saveAsTable("table1_as_parquet")
```

**Example - output as Delta table**
Creating a [[2.1 Delta Lake for Spark]] table uses almost identical syntax – it’s as easy as switching your format from "parquet" to "delta":
```
df.write.format("delta").saveAsTable("table1")
```

**Example - Partitioning the output file**
Partitioning is an optimization technique that enables Spark to maximize performance across the worker nodes. More performance gains can be achieved when filtering data in queries by eliminating unnecessary disk IO.
```
bikes_df.write.partitionBy("Category").mode("overwrite").parquet("Files/bike_data")
```


Also see 
- [[Spark catalog and SQL query]]
- [[visualization in spark notebook]]
- [[Work with delta tables in Spark]]