# RDS data security

- SSL/TLS (in transit) can be mandatory
- RDS supports EBS volume encryption with KMS
- handled by host/ EBS
- AWS/ customer managed CMK generates data key for encryption operation
- storage, logs, snapshots & replicas are encrypted
- …encryption can’t be removed

**Special**

[[RDS data security/Untitled.png]]

RDS MSQL & Oracle support transparent data encryption (TDE), encrypted within the DB engine

- Oracle can use key from cloudHSM
- much stronger key controls

**IAM authentication & authorization**

[[RDS data security/Untitled 1.png]]

- don't need to use a password when you connect to a DB instance. Instead, you use an authentication token, which is a unique string of characters that Amazon RDS generates on request
- authentication handle with IAM, IAM role allow the DBuser to request token
- authorization handled inside RDS not related to IAM
