---
title: Amazon Appflow
tags:
  - aws
---

# Amazon Appflow

- a fully managed integration service that enables users to securely exchange data between different SaaS including AWS (don't spend time writing integration s and leverage API immediately)
    - sync data across applications
	    - Sources: Salesforce, SAP, Slack, ServiceNow...
		- Destination: S3, redshift, snowflake, Salesforce...
    - aggregation data from different sources, avoid data silos
    - Data transformation like filtering and validation
- Encrypted over public internet, but works with privateLink over AWS
- can use Appflow custom connector SDK

[[Amazon Appflow/Untitled.png]]

- configure source & destination connection (can be reused)
- source to destination field mapping which to which
- filer and validation select what to flow through
