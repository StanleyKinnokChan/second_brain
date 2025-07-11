#### AWS EMR





Security
- attach IAM roles to EC2 instances (S3, EMRFS request to S3, dynamoDB scans through Hive)
- EC2 SGs 
	- one for master node
	- another one for cluster node
- Kerboeros Authentication from Active Directory
- Apache Ranger: Centralized Authorization (RBAC) - setup on external EC2
- Encryption
	- At-rest data encryption for EMRFS
		- Encryption in S3 
			- SSE-S3, SSE-KMS, client-side encryption)
		- Encryption in local disk
			- open-source HDFS encryption
			- EC2 instance store encryption (NVMe/ LUKS)
			- EBS volumes
				- EBS encryption (KMS) - works with root volume
				- LUKS encryption - does not work with root
	- In-transit encryption
		- node to node communication
		- For EMRFS traffic between S3 and cluster nodes
		- TLS encryption

![[EMR security.png]]