# Amazon Athena

[[Amazon Athena/Untitled.png]]

- serverless querying service
- ad-hoc queries on data in S3 - pay only data consumed
- **schema-on-read** - provide **table-like translation**, where **original data in S3 remains unchanged**
- no infrastructure itself, just a translation service without loading/ transformation
- **querying logs (**AWS logs/ glue data catalog/ web server logs)
- **Athena federated query**…other data sources as well that is not S3
