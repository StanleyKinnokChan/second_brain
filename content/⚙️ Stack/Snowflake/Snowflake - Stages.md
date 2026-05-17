---
title: Snowflake - Stages
tags:
  - snowflake
---
**External stage:** 
- Storage location outside [[Snowflake]] (e.g., [[AWS S3]], Azure Blob, Google Cloud Storage) linked to [[Snowflake]] for accessing external files.

**Internal stage:** 
- Storage managed by [[Snowflake]] within its system, used for temporary or permanent file storage directly inside [[Snowflake]]. 
- Primarily used for staging files locally within Snowflake’s managed storage —like uploading files from your local machine to Snowflake before loading them into tables.
- [Internal stage parameters](https://docs.snowflake.com/en/sql-reference/sql/create-stage#internal-stage-parameters-internalstageparams) specifies the type of encryption supported for all files stored on the stage. Type:
	- `SNOWFLAKE_FULL`: Client-side and server-side encryption
	- `SNOWFLAKE_SSE`: Server-side encryption only.


Snowflake internal stages come in three types with different uses:
1. **User Stage** (referenced using `@~`)
* Dedicated to each user automatically.
* Temporary storage for files a user uploads or downloads.
* Use case: Quick, personal file staging for ad-hoc loads or unloads.

2. **Table Stage** (referenced using `@%`)
* Automatically created for each table.
* Tied to a specific table, used mainly for loading data directly into that table.
* Use case: Temporary storage during bulk data loading operations for a table.

3. **Named Internal Stage** (referenced using `@`)
* Explicitly created by users.
* Can be shared and reused across users and sessions.
* Use case: Centralized staging area for common files, reusable by multiple users or processes.


Use  `DESC STAGE` to see the stage setting
[File functions](https://docs.snowflake.com/en/sql-reference/functions-file) enable you to access files staged in cloud storage.