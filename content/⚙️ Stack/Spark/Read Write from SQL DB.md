---
title: 
tags:
  - spark
---
### Connection
By using jdbc, spark can connect to SQL DB
```
driver = "org.sqlite.JDBC"
path = "/data/flight-data/jdbc/my-sqlite.db"
url = "jdbc:sqlite:" + path
tablename = "flight_info"

dbDataFrame = spark.read.format("jdbc").option("url", url)\
.option("dbtable", tablename).option("driver", driver).load()
```


### Query Pushdown
- can be achieved by providing a query 
```
pushdownQuery = """(SELECT DISTINCT(DEST_COUNTRY_NAME) FROM flight_info)
AS flight_info"""
dbDataFrame = spark.read.format("jdbc")\
.option("url", url).option("dbtable", pushdownQuery).option("driver", driver)\
.load()
```

### Read data in parallel
- can be achieved by providing the (1) number of partitions or (2) predicates or (3) sliding window
- Multiple executors cannot read from the same file at the same time necessarily, but they can read different files at the same time.
```
# method 1
dbDataFrame = spark.read.format("jdbc")\
.option("url", url).option("dbtable", tablename).option("driver", driver)\
.option("numPartitions", 10).load()

# method 2
props = {"driver":"org.sqlite.JDBC"}
predicates = [
"DEST_COUNTRY_NAME = 'Sweden' OR ORIGIN_COUNTRY_NAME = 'Sweden'",
"DEST_COUNTRY_NAME = 'Anguilla' OR ORIGIN_COUNTRY_NAME = 'Anguilla'"]
spark.read.jdbc(url, tablename, predicates=predicates, properties=props).show()
spark.read.jdbc(url,tablename,predicates=predicates,properties=props)\
.rdd.getNumPartitions() # 2

#method 3
colName = "count"
lowerBound = 0L
upperBound = 348113L # this is the max count in our database
numPartitions = 10

spark.read.jdbc(url, tablename, column=colName, properties=props,
lowerBound=lowerBound, upperBound=upperBound,
numPartitions=numPartitions).count() # 255
```

### Write
- The number of files or data written is dependent on the number of partitions the DataFrame has at the time you write out the data.
```
newPath = "jdbc:sqlite://tmp/my-sqlite.db"

# mode: overwrite/append
csvFile.write.jdbc(newPath, tablename, mode="overwrite", properties=props)
```

