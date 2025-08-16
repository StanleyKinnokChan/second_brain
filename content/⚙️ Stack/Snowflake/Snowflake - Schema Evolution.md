---
title: 
tags:
  - Snowflake
---
Semi-structured data tends to evolve over time. Systems that generate data add new columns to accommodate additional information, which requires downstream tables to evolve accordingly.

1. **INFER SCHEMA**
	- The schema infers when loading in a file, so it is schema-on-read
```
-- Create a file format that sets the file type as Parquet.  
CREATE OR REPLACE FILE FORMAT my_json_format  
TYPE = json,  
STRIP_OUTER_ARRAY=TRUE;  
  
  
-- Query the INFER_SCHEMA function.  
--- the JSON file name is "json_sample_v1.json" & The file format is "my_json_format"  
SELECT *  
FROM TABLE(  
INFER_SCHEMA(  
LOCATION=>'@stage_for_json/json_sample_v1.json'  
, FILE_FORMAT=>'my_json_format'  
)  
);
```


2. **enable_schema_evolution=true**
	- as a table setting
	- new data loads in -> the columns will be updated
```
--enable for the schema evolution  
alter table demo_json_table_v1 set enable_schema_evolution=true;

--Load the table with new column using the COPY INTO command, a new column will be added
COPY INTO demo_json_table_v1  
FROM '@stage_for_json/'  
FILES=('json_file_2.json')  
FILE_FORMAT=my_json_format  
match_by_column_name=case_insensitive ---This is the important step  
purge=true;
```





https://docs.snowflake.com/en/user-guide/data-load-schema-evolution