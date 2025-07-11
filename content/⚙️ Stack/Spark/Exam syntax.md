---
title: 
tags:
  - spark
  - exam
---

- If a column was subjected to tranformation, col() is needed. If a column just served as a reference point (e.g. groupBy, drop_duplicates, partitionBy...), col() is not needed
- subset is used is we put the column(s) into main df function as argument, which could be the column string or column string list. 
- agg function will either be used for the whole df, or used with the agg()/ groupBy() function
- .read/write don't need a (), it is an object required other functions
- some method are columns object specific (e.g. .cast(), .alias(), .contains() )
- some functions are imported (e.g. upper(), lit(), explode(), split() )

Transformation
```
# createdataframe
df = spark.createDataFrame(
    [(1,2,3,4),(5,6,7,8)],    # list of rows
    ["id1", "id2", "id3","id4"] # list of columns name
)
 
# column rename (must be done one by one)
df.withColumnRenamed("existing", "new")

# filter condition needs to be in bracket (|or &and ~not)
df.filter((col("sqft") <= 25000) | (col("customerSatisfaction") >= 30)) # Alias .where()

# new formular of new column
df.withColumn("employeesPerSqft", col("numberOfEmployees") / col("sqft"))

# cast datatype
df.withColumn("storeId, col("storeId").cast(StringType()))

# constant as new column
df.withColumn("modality", lit("PHYSICAL"))

# split column 
df.withColumn("storeValueCategory", split(col("storeCategory"), "_")[0])  
.withColumn("storeSizeCategory", split(col("storeCategory"), "_")[1]))

# explode array
df.withColumn("productCategories", explode(col("productCategories")))

# replace string
df.withColumn("storeDescription", regexp_replace(col("storeDescription"), "<string_old>", "<string_new>"))

# drop all duplications
- DataFrame.distinct()
- DataFrame.dropDuplicates() # alias
- DataFrame.drop_duplicates() # alias
- DataFrame.drop_duplicates(subset = None) #subset = drop per group, either non or column list. Only first records in the group will be kept

# fill na
df.na.fill("unknown",["city"]) # has to be a column string/ string list 
df.fillna() # alias

# drop na (if empty row then "all", if any missing then "any")
df.na.drop(how="All") 

# drop column
df.drop(<col1>) # no-op if no col is given 

# approx_count_dictinct, agg function is a must
df.agg(approx_count_distinct(col("division"), 0.15).alias("divisionDistinct")) # the number is the allowed standard deviation, the higher the faster

# return a mean
df.agg(mean(col("sqft")).alias("sqftMean"))

# returns a GroupedData object (column format is flexible)
df.groupBy(“division”, “storeCategory”)
df.groupBy().mean()

# reverse sorted alphabetically
df.orderBy(col("division").desc())

# sample 15% data with replacement
df.sample(True, fraction=0.15)

# change from UNIX eapoch format to Java's simpledateformat  
df.withColumn("openDateString", from_unixtime(col("openDate"), "EEE, MMM d, yyyy h:mm a") # result: "Sunday, Dec 4, 2008 1:05 PM"

# get dateofyear/month/quarter... from a timestamp, must not from the UNIX epoch, so cast first
df.withColumn("openTimestamp", col("openDate").cast("Timestamp"))  
.withColumn("dayOfYear", dayofyear(col("openTimestamp")))

# join( df, condition, method)
df.join(df2, "name", 'inner')
df.join(df2, [df.name == df2.name], 'outer')
df.join(df2, df["name"] == df2["name"], "inner")

# cross join 
df.crossJoin(df2).show()

# union (default by position, alias: unionall) 
df1.union(df2)

# union (by name)
df1.unionByName(df2)

# first two characters of column
df.withColumn(“division”, col(“division”).substr(0, 2))

# extracts the value for column sqft from the first row of
df.first().column_name
```

**I/O**
```
# read 
spark.read.load(df = spark.read.format("csv").option("header", "true").load("path/to/file.csv") # generic
df = spark.read.csv("path/to/file.csv", header=True) # format specific

# read with schema object
spark.read.schema(schema).format("json").load(filePath)

# writes df to filePath as JSON
df.write.json(filePath) 

# write df to filePath as Parquet, partitioning by col1 
df.write.partitionBy('col1').parque(filePath)

# overwrite mode output as text
df.write.mode("overwrite").text(filePath)
```

Properties Config 
```
# control partitions that do not meet a minimum size threshold are automatically coalesced into larger partitions during a shuffle
spark.sql.adaptive.coalescePartitions.enabled

# maximum size of an automatically broadcasted DataFrame when performing a join
spark.sql.autoBroadcastJoinThreshold

# skewed partitions are automatically detected and subdivided into smaller partitions when joining two DataFrames together
spark.sql.adaptive.skewedJoin.enabled

# adjust the number of partitions used in wide transformations like join()
spark.sql.shuffle.partitions
```

Others
```
# cache the partitions of DataFrame df only in Spark’s memory
df.persist(StorageLevel.MEMORY_ONLY).count()

# sql query
df.createOrReplaceTempView("df_view")
spark.sql("select * from df_view")

# printSchema
df.printSchema()

# register udf
spark.udf.register("<udf_name>", func, "STRING") # UDF with Spark SQL
<udf_name> = udf(func, return_type e.g. integertype() ) # UDF for use within the DataFrame API

# apply udf
df = spark.sql("SELECT udf_name(column_name) FROM some_table") #sparksql
df = df.withColumn("performance", udf_name(col("column_name")) )

# summary statistics for all/specifc columns
df.describe()
df.describe(["name","age"]).show()

# applies the function assessPerformance() to each row of DataFrame df
 [assessPerformance(row) for row in df.collect()]
```
