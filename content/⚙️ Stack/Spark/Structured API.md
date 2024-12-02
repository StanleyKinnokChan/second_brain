---
title: 
tags:
  - spark
---
The Structured APIs are a tool for manipulating all sorts of data, from unstructured log files to semi-structured CSV files and highly structured Parquet files. These APIs refer to three core types of distributed collection
APIs:
- Datasets (only for JVM based lanuages, NA for pyspark)
- DataFrames
- SQL tables and views

Dataframe and datasets are immutable, typed and lazily evaluated plans
most of them applied for b
]oth batch and streaming (little to no effort for migration)

Their types can be manually defined or schema on read (see [[Schema on writes & on read]]). Spark use Catalyst to maintains type information throughout the planning and processing. So the operation is purely in Spark but not python.

dataframe = dataset of type ROW -> optimized in-memory format for computation, with type checked during runtime (vs. during compile time in datasets)

See :
- how the [[Structured API Execution]] performs
- [[Structured operations (basic)]]
- 