---
title: 
tags:
  - spark
---
columns are logical constructions that simply represent a value computed on a prerecord
basis by means of an expression.

Columns exists only have real values (row) within dataframe

Column might or might not exist in our DataFrames. Columns are not resolved until we compare the column names with those we are maintaining in the catalog

Column and table resolution happens in the analyzer phase

columns are expressions - a set of transformations on one or more values in a record in a DataFrame

Column can be referenced by `col()`
Column can be transformed in multiple steps
```
from pyspark.sql.functions import expr
expr("(((someCol + 5) * 200) - 6) < otherCol")
```
Column list in a dataframe can be accessed via `.columns`
