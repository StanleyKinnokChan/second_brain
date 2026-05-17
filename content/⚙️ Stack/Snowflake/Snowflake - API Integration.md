---
title: Snowflake - API Integration
tags:
  - snowflake
---
In [[Snowflake]], **API integration** is a security object that lets [[Snowflake]] securely call out to an external service through an **external function**. It is needed when creating an external function

### Breakdown:

- **External function**: A [[Snowflake]] function whose logic runs outside [[Snowflake]] (e.g., [[AWS Lambda]], Azure Function, or Google Cloud Function).

- **API integration**: Defines the _trust relationship_ between Snowflake and the cloud provider service. It tells Snowflake:
    - Which cloud platform to use (`AWS_API_GATEWAY`, `AZURE_API_MANAGEMENT`, `GCP_API_GATEWAY`).
    - Which API endpoint Snowflake is allowed to call.
    - The IAM role or service principal Snowflake assumes to authenticate the call.

Flow:
1. You create the API integration object.
2. You create an external function in Snowflake that references this integration.
3. When the function is called in SQL, Snowflake routes the request to the external API securely.