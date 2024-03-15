# AWS DataSync

[[AWS DataSync/Untitled.png]]

- **data transfer service between AWS and SAN/NAS storage**
- for migrations, data processing transfers, archival, DR/BC
- ..designed to work at huge scale (~100TB per day)
- keeps **metadata** (eg permission/ timestamps)
- built in **data validation** (data arrived AWS match the origin)
- **bandwidth limiter**
- **incremental**/ **schedule** options
- **compression** and **encryption**
- **automatic recovery** from transit errors
- AWS service integration - S3, EFS, FSx
- pay as you use per GB

**Terminology**

[[AWS DataSync/Untitled 1.png]]
