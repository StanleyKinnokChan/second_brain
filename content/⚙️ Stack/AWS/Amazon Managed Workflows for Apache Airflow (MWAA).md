---
title: Amazon Managed Workflows for Apache Airflow (MWAA)
tags:
  - aws
---

#### Amazon Managed Workflows for Apache Airflow (MWAA)
- batch-orientaed workflow tool
- defined workflos as python code to create DAG
- MWAA managed service for apache airflow
- use cases:
	- Complex workflows
	- ELT pipeline
- DAGs are uploaded into S3 (may also zip it with required plugin and requirements), which is picked up by MWAA
- runs within a VPC
- Private or public endpoint
- Automatic scaling of workers based on queue backlog
- scheduler and workers are fargate containers

Integration
- leverage open-source integration