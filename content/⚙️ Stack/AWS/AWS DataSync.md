# AWS DataSync

[[AWS DataSync/Untitled.png]]

- Move large amount of data to and from
	- On-premises / other cloud to AWS (NFS, SMB, HDFS, S3 API…) – needs agent
	- AWS to AWS (different storage services) – no agent needed
- for migrations, data processing transfers, archival, DR/BC
- Replication tasks can be scheduled hourly, daily, weekly (have lagging)
- ..designed to work at huge scale (~100TB per day)
- **File permissions and metadata** are preserved (NFS POSIX, SMB…)
- built in **data validation** (data arrived AWS match the origin)
- **bandwidth limiter**
- **incremental**/ **schedule** options
- **compression** and **encryption**
- **automatic recovery** from transit errors
- AWS service integration - S3, EFS, FSx
- pay as you use per GB
- have to use snowcone if no internet
- 
![[AWS DataSync.png]]

![[Pasted image 20250619174721.png]]