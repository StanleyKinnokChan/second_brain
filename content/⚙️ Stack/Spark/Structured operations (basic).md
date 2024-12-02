---
title: 
tags:
  - spark
---
see what is [[columns in spark]] and [[rows in spark]]

selecting columns
```
df.selectExpr(
"*", # all original columns
"(DEST_COUNTRY_NAME = ORIGIN_COUNTRY_NAME) as withinCountry")\
.show(2)
```

Literals:
- provide a mean to supply the constant value for comparisons/ transformation logic
```
from pyspark.sql.functions import lit
df.select(expr("*"), lit(1).alias("One")).show(2)

+-----------------+-------------------+-----+---+
|DEST_COUNTRY_NAME|ORIGIN_COUNTRY_NAME|count|One|
+-----------------+-------------------+-----+---+
| United States| Romania| 15| 1|
| United States| Croatia| 1| 1|
+-----------------+-------------------+-----+---+
```

adding/ rename columns:
```
df.withColumn("numberOne", lit(1)).show(2)
df.withColumnRenamed("DEST_COUNTRY_NAME", "dest").columns
```

By default Spark is case insensitive; however, you can make Spark case sensitive by setting the
configuration via `set spark.sql.caseSensitive true`

Removing Columns
```
#  dedicated method called drop:
df.drop("ORIGIN_COUNTRY_NAME").columns

#We can drop multiple columns by passing in multiple columns as arguments:
df.drop("ORIGIN_COUNTRY_NAME", "DEST_COUNTRY_NAME")
```

Changing a Column’s Type (cast)
```
--in dataframe
df.withColumn("count2", col("count").cast("long"))

-- in SQL
SELECT *, cast(count as long) AS count2 FROM dfTable
```

filter (use filter/where keyword = the same)
```
df.filter(col("count") < 2).show(2)
df.where("count < 2").show(2)

# multiple conditions (all work; spark do filtering at once)
df.filter((col("act_date") >= "2016-10-01") & (col("act_date") <= "2017-04-01"))
df.filter("act_date >='2016-10-01' AND act_date <='2017-04-01'")
df.filter("act_date <='2017-04-01'").filter("act_date >='2016-10-01'")

-- in SQL
SELECT * FROM dfTable WHERE count < 2 LIMIT 2
```

Getting Unique Rows
```
# .distinct() returns dataframe
df.select("ORIGIN_COUNTRY_NAME", "DEST_COUNTRY_NAME").distinct().count()
df.select("ORIGIN_COUNTRY_NAME").distinct()

-- in SQL
SELECT COUNT(DISTINCT(ORIGIN_COUNTRY_NAME, DEST_COUNTRY_NAME)) FROM dfTable
```

Random Samples
```
seed = 5
withReplacement = False
fraction = 0.5
df.sample(withReplacement, fraction, seed).count()
```

Random Splits
```
dataFrames = df.randomSplit([0.25, 0.75], seed)
dataFrames[0].count() > dataFrames[1].count() # False
```

Union
- To union two DataFrames, you must be sure that they have the same schema and number of columns; otherwise, the union will fail.
```
df.union(newDF)
```

Sorting Rows:
- The default is to sort in ascending order
- need desc asc method if we want to speify the order
- `asc_nulls_first, desc_nulls_first, asc_nulls_last, or desc_nulls_last` to deal with the sorting order with nulls
```
from pyspark.sql.functions import desc, asc
df.orderBy(expr("count desc")).show(2)
df.orderBy(col("count").desc(), col("DEST_COUNTRY_NAME").asc()).show(2)
```

limit:
```
# in Python
df.orderBy(expr("count desc")).limit(6).show()

-- in SQL
SELECT * FROM dfTable ORDER BY count desc LIMIT 6
```

Repartition and Coalesce:
- Repartition will incur a full shuffle of the data
- Coalesce, on the other hand, will not incur a full shuffle and will try to combine partitions.
```
df.rdd.getNumPartitions()
df.repartition(5)

# if you know which columns always being filtered
df.repartition(col("DEST_COUNTRY_NAME"))
df.repartition(5, col("DEST_COUNTRY_NAME")) # specify the partition number as well

# coalesce the partitioned data
df.repartition(5, col("DEST_COUNTRY_NAME")).coalesce(2)
```

Collecting Rows:
- running take or head requires moving data into the application’s driver process, and doing so with  a very large and can crash the driver process
```
# in Python
collectDF = df.limit(10) #New DataFrame as an transformation, could takes longer
collectDF.take(5) # selects the first N rows in array
collectDF.show() # this prints it out nicely
collectDF.show(5, False) 
collectDF.collect()
```

