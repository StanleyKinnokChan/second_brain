---
title: Amazon Athena
tags:
  - aws
---

# Amazon Athena

[[Amazon Athena/Untitled.png]]

- serverless querying service
- ad-hoc queries on data in S3 - pay only data consumed
- **schema-on-read** - provide **table-like translation**, where **original data in S3 remains unchanged**
- no infrastructure itself, just a translation service without loading/ transformation
- **querying logs (**AWS logs/ glue data catalog/ web server logs)
- **Athena federated query**…other data sources as well that is not S3

security:
- IAM policies
- at rest: data is S3 (inherent S3 encryption)
- in transit: using TLS between Athena and S3 and JDBC
- fine grained access using the AWS glue catalog