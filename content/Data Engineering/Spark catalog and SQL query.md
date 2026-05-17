---
title: Spark catalog and SQL query
tags:
  - data-engineering
  - spark
---
**Dataframe API** is part of a [[Spark]] library named **[[Spark]] SQL**, which enables data analysts to use SQL expressions to query and manipulate data.
**[[Spark]] catalog** is a metastore for relational data objects such as views and tables


One of the simplest ways to make data in a dataframe available for querying in the [[Spark]] catalog is to create a temporary view, as shown in the following code example:
```
df.createOrReplaceTempView("products_view")
```

You can create an empty table by using the `spark.catalog.createTable` method, or you can save a dataframe as a table by using its `saveAsTable` method. Deleting a managed table also deletes its underlying data.
```
df.write.format("delta").saveAsTable("products")
```

## Using the Spark SQL API to query data
```
# uses a SQL query to return data from the **products** table as a dataframe.

bikes_df = spark.sql("SELECT ProductID, ProductName, ListPrice \
                      FROM products \
                      WHERE Category IN ('Mountain Bikes', 'Road Bikes')")
display(bikes_df)
```

## Using SQL code
The previous example demonstrated how to use the Spark SQL API to embed SQL expressions in Spark code. In a notebook, you can also use the `%%sql` magic to run SQL code that queries objects in the catalog, like this:
```
%%sql 
SELECT Category, COUNT(ProductID) AS ProductCount FROM products GROUP BY Category ORDER BY Category
```