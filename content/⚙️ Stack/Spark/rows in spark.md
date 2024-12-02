---
title: 
tags:
  - spark
---
each row in a DataFrame is a single record. Spark represents this record as an object of
type **Row**

only DataFrames have schemas. Rows themselves do not have
schemas. This means that if you create a Row manually, you must specify the values in the same
order as the schema of the DataFrame to which they might be appended

```
from pyspark.sql import Row
myRow = Row("Hello", None, 1, False)

# access value of columns in a row, by position
df.first()[1]
```

