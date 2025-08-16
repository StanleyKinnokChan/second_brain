---
title: 
tags:
  - Snowflake
---
Snowflake supports bulk export (i.e. unload) of data from a database table into flat, delimited text files.

Steps:
- table unload to stage
- download file from stage

```
-- To the named stage
COPY INTO @%mytable/unload/ from mytable FILE_FORMAT = (FORMAT_NAME = 'my_csv_unload_format' COMPRESSION = NONE);
--then download the files
GET @mystage/unload/data_0_0_0.csv.gz file://C:\data\unload;


-- To S3
COPY INTO 's3://mybucket/unload/'
  FROM mytable
  STORAGE_INTEGRATION = s3_int;
```


https://docs.snowflake.com/en/user-guide/data-unload-overview