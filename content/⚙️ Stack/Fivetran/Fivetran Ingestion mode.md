---
title: Fivetran Ingestion mode
tags:
  - fivetran
---
### Soft Delete Mode (Default)
- marks rows as deleted in the destination after they are deleted in the source (key doesn't exist => fivetran_deleted changes to true)
- if key appears again (fivetran_delete changes back to false, with a new value)
- This means the delete history won't exist
### History Mode (SCD2)
- recording _every version of each record in the source table
- _fivetran_active, _fivetran_start, _fivetran_end