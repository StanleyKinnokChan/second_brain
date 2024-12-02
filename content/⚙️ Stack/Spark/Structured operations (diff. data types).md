---
title: 
tags:
  - spark
---
#### Booleans
```
df.where(col("InvoiceNo") != 536365)\
.select("InvoiceNo", "Description")

# chain filter with condition as variable
from pyspark.sql.functions import instr
priceFilter = col("UnitPrice") > 600
descripFilter = instr(df.Description, "POSTAGE") >= 1
df.where(df.StockCode.isin("DOT")).where(priceFilter | descripFilter).show()

# booleans to filter columns

# use columns in where clause to filter rows (filter to true) 
df.withColumn("isExpensive", DOTCodeFilter & (priceFilter | descripFilter))\
.where("isExpensive")\
.select("unitPrice", "isExpensive").show(5)
```

#### Numbers
```
# different funciton for calcaultion purpose
from pyspark.sql.functions import expr, pow
fabricatedQuantity = pow(col("Quantity") * col("UnitPrice"), 2) + 5
df.select(expr("CustomerId"), fabricatedQuantity.alias("realQuantity")).show(2)

# round, bottom bround
from pyspark.sql.functions import lit, round, bround
df.select(round(lit("2.5")), bround(lit("2.5"))).show(2)

# correlation
from pyspark.sql.functions import corr
df.stat.corr("Quantity", "UnitPrice")
df.select(corr("Quantity", "UnitPrice")).show()

# describe statistic
df.describe().show()

# aggregation method
from pyspark.sql.functions import count, mean, stddev_pop, min, max

# generate id
from pyspark.sql.functions import monotonically_increasing_id
df.select(monotonically_increasing_id()).show(2)
```

#### Strings
```
# capatical every words seperated by a space
from pyspark.sql.functions import initcap
df.select(initcap(col("Description"))).show()

# upper case/ lower case
from pyspark.sql.functions import lower, upper
df.select(col("Description"),
lower(col("Description")),
upper(lower(col("Description")))).show(2)

# trim & pad
from pyspark.sql.functions import lit, ltrim, rtrim, rpad, lpad, trim
df.select(
ltrim(lit(" HELLO ")).alias("ltrim"),
rtrim(lit(" HELLO ")).alias("rtrim"),
trim(lit(" HELLO ")).alias("trim"),
lpad(lit("HELLO"), 3, " ").alias("lp"),
rpad(lit("HELLO"), 10, " ").alias("rp")).show(2)
```

#### Regex
```
# replace
from pyspark.sql.functions import regexp_replace
regex_string = "BLACK|WHITE|RED|GREEN|BLUE"
df.select(
regexp_replace(col("Description"), regex_string, "COLOR").alias("color_clean"),
col("Description")).show(2)

# replace character by each ordered characters
from pyspark.sql.functions import translate
df.select(translate(col("Description"), "LEET", "1337"),col("Description"))\
.show(2)

# regexp_extract
extract_str = "(BLACK|WHITE|RED|GREEN|BLUE)"
df.select(
regexp_extract(col("Description"), extract_str, 1).alias("color_clean"),
col("Description")).show(2)
```


#### Datetime:
- Spark is working with Java dates and timestamps
- Spark’s TimestampType class supports only second-level precision. you’ll need to work around this problem by potentially operating on them as longs.
- You can set a session local timezone if necessary by setting spark.conf.sessionLocalTimeZone
- Spark will not throw an error if it cannot parse the date; rather, it will just return null
```
from pyspark.sql.functions import current_date, current_timestamp
dateDF = spark.range(10)\
.withColumn("today", current_date())\
.withColumn("now", current_timestamp())
dateDF.createOrReplaceTempView("dateTable")
dateDF.printSchema()

# add/subtract date
from pyspark.sql.functions import date_add, date_sub, col
dateDF.select(date_sub(col("today"), 5), date_add(col("today"), 5)).show(1)

# calculation of date/ string to date
from pyspark.sql.functions import datediff, months_between, to_date
dateDF.withColumn("week_ago", date_sub(col("today"), 7))\
  .select(datediff(col("week_ago"), col("today"))).show(1)

dateDF.select(
    to_date(lit("2016-01-01")).alias("start"),
    to_date(lit("2017-05-22")).alias("end"))\
  .select(months_between(col("start"), col("end"))).show(1)

# string to date with specific format using to_timestamp()/ to_date()
from pyspark.sql.functions import to_date
dateFormat = "yyyy-dd-MM"
cleanDateDF = spark.range(1).select(
to_date(lit("2017-12-11"), dateFormat).alias("date"),
to_date(lit("2017-20-12"), dateFormat).alias("date2"))
cleanDateDF.createOrReplaceTempView("dateTable2")

# date comparison
cleanDateDF.filter(col("date2") > lit("2017-12-12")).show()
```

#### Nulls
- The primary way of interacting with null values, at DataFrame scale, is to use the .na subpackage on a DataFrame
- There are two things you can do with null values: you can explicitly drop nulls or you can fill them with a value (globally or on a per-column basis)
```
# return first non-null value from a set of columns
from pyspark.sql.functions import coalesce
df.select(coalesce(col("Description"), col("CustomerId"))).show()

# removes rows that contain nulls
df.na.drop()
df.na.drop("any") # any values
df.na.drop("all") # only if all values are null
df.na.drop("all", subset=["StockCode", "InvoiceNo"]) # set of column with null

# fill the null
df.na.fill("All Null values become this string")
df.na.fill("all", subset=["StockCode", "InvoiceNo"])

# fill the nulll with column:values mapping
fill_cols_vals = {"StockCode": 5, "Description" : "No Value"}
df.na.fill(fill_cols_vals) # map the column
```

#### struct
- like a df within a df
```
# created by:
from pyspark.sql.functions import struct
complexDF = df.select(struct("Description", "InvoiceNo").alias("complex"))

# select using a dot or method .getfield(), using * for all vales
complexDF.select("complex.Description")
complexDF.select(col("complex").getField("Description"))
complexDF.select("complex.*")
```

Array
```
# split text with delimeter into array
from pyspark.sql.functions import split
df.select(split(col("Description"), " ")).show(2)

# array position can be queried
df.select(split(col("Description"), " ").alias("array_col"))\
.selectExpr("array_col[0]").show(2)

# check array length using size()
from pyspark.sql.functions import size
df.select(size(split(col("Description"), " "))).show(2)

# check array contains a value, returns boolean
from pyspark.sql.functions import array_contains
df.select(array_contains(split(col("Description"), " "), "WHITE")).show(2)

# explode array into rows
from pyspark.sql.functions import split, explode
df.withColumn("splitted", split(col("Description"), " "))\
.withColumn("exploded", explode(col("splitted")))\
.select("Description", "InvoiceNo", "exploded").show(2)
```


#### Map
```
# create map
from pyspark.sql.functions import create_map
df.select(create_map(col("Description"), col("InvoiceNo")).alias("complex_map"))\
.show(2)

# query
df.select(map(col("Description"), col("InvoiceNo")).alias("complex_map"))\
.selectExpr("complex_map['WHITE METAL LANTERN']").show(2)

# explode the map into column
df.select(map(col("Description"), col("InvoiceNo")).alias("complex_map"))\
.selectExpr("explode(complex_map)").show(2)
```

#### Json
```
# demo json
jsonDF = spark.range(1).selectExpr("""
'{"myJSONKey" : {"myJSONValue" : [1, 2, 3]}}' as jsonString""")

# get json value
from pyspark.sql.functions import get_json_object, json_tuple
jsonDF.select(
get_json_object(col("jsonString"), "$.myJSONKey.myJSONValue[1]") as "column",
json_tuple(col("jsonString"), "myJSONKey")).show(2) #

# struct to json
from pyspark.sql.functions import to_json
df.selectExpr("(InvoiceNo, Description) as myStruct")\
.select(to_json(col("myStruct")))
```