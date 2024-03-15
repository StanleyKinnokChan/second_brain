# AWS Glue

[[AWS Glue/Untitled.png]]

- serverless ETL (vs data pipeline using servers - EMR)
- crawls data sources and generates the **AWS glue data catalog**, help data visibility for whole organization
- cost effective
- **source - store**: S3, RDS, JDBC, dynamoDB
- **source - stream:** kinesis data stream, apache Kafka
- **target**: S3, RDS, JDBC databases

<aside>
💡 ***JDBC*** stands for Java ***Database*** Connectivity. ***JDBC*** is a Java API to connect and execute the query with the ***database***.

</aside>

**data catalog**

- persistent **metadata** about data sources in region
- 1 catalog per region per account, avoids **data silos**
- used by amazon athena, redshift, EMR, lake formation

<aside>
💡 A data silo is **a collection of data held by one group that is not easily or fully accessible by other groups in the same organization**

</aside>
