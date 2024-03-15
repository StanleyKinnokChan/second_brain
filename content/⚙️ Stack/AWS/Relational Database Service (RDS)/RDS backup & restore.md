# RDS backup & restore

[[RDS backup & restore/Untitled.png]]

[[RDS backup & restore/1_X2x-kL7ujebuv4FJodZcuQ.webp]]

**Backup**

- 2 methods
    - automated backups
        - from a standby
        - with every 5 minutes transaction logs (recovery point)
        - old backup would not be retained (can set retention period 0-35 days)
    - manual snapshots
        - backup all the database (1st snap is full backup, then onward is incremental)
        - snapshot don’t expire - you have to delete them manually
- use AWS managed S3 buckets - cannot be seen in console UI
    - replicated across AZs
- replicated backup to other another region - in form of snapshots & transaction logs

**Restore**

- creates a **NEW RDS instance** with **new address**
- snapshots = single point in time (manual)
- automate any 5 minute point in time
- back to the RPO
- restores aren’t fast - think about RTO
