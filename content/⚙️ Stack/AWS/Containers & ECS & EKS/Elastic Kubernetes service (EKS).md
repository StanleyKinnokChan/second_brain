# Elastic Kubernetes service (EKS)

[Introduction of Kubernetes](Elastic%20Kubernetes%20service%20(EKS)%2037fe74f8ddb540b98db7750a63f36ef2/Introduction%20of%20Kubernetes%2082ed44ad852a485caa0ee385f5b31e7f.md)

- AWS managed Kubernetes - open source & cloud agnostic
- can run in AWS, outposts, EKS anywhere, EKS distro..
- control plane scales and runs on multiple AZs
- integrates with AWS services (ECR, ELB, IAM, VPC…)
- EKS cluster = EKS control Plane & EKS nodes
- etcd distributed across multiple AZs
- Nodes - self managed, managed node groups or fargate pods
- storage provider - can be EBS, EFS, FSx…

**Architecture:**

[[Elastic Kubernetes service (EKS]]%2037fe74f8ddb540b98db7750a63f36ef2/Untitled.png)

- control plane communicate via ENIs or public endpoint
