
- Amazon EKS = Amazon Elastic Kubernetes Service
- launch managed Kubernetes clusters on AWS
- It’s an alternative to ECS, similar goal but different API
- EKS supports EC2 if you want to deploy worker nodes or Fargate to deploy serverless containers
- Use case: if your company is already using Kubernetes on-premises or in another cloud, and wants to migrate to AWS using Kubernetes
- Collect logs and metrics using CloudWatch Container Insights


Data Volumes
- Need to specify **StorageClass** manifest on your EKS cluster
- Leverages a **Container Storage Interface (CSI)** compliant driver
- Support for…
	- EBS
	- EFS (Fargate only)
	- FSx for Lustre
	- FSx for NetApp ONTAP