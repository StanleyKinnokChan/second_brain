---
title: AWS — Index
tags:
  - aws
  - moc
---

> [!info] Map of Content
> This page is the entry point to every AWS note in this vault. Notes are grouped by service category so related concepts sit next to each other.

## Foundations

- [[AWS]] — what AWS is, at a glance
- [[Introduction of AWS]] — overview & history
- [[Concept of tools and services]]
- [[AWS global infrastructure]] — regions, AZs, edge locations
- [[AWS Local Zones]]
- [[edge and hybrid computing services]]
- [[High-Availability vs Fault-Tolerance vs Disaster Recover]]
- [[Architecture Design]]
- [[Good features for architecture]]

## Compute

- [[EC2]] — virtual servers (see EC2 deep dives below)
- [[AWS Lambda]] — serverless functions
- [[AWS Batch]] — batch compute jobs
- [[AWS Serverless Application Model]] (SAM)
- [[Auto Scaling Group]] — horizontal scaling
- [[Load balancers]] — ALB / NLB / GWLB / CLB

### EC2 deep dives

- [[Amazon Machine Image (AMI)]]
- [[EC2 Instance Type]]
- [[EC2 Purchase Options]]
- [[EC2 instance store]]
- [[EBS and instance Storage]]
- [[Bootstrapping using User Data]]
- [[Connection]] — connecting to EC2
- [[Enhanced networking & EBS Optimized]]
- [[Instance Metadata]]
- [[Instance Roles & Profile]]
- [[Instance status checks, Auto-recovers & Termination]]
- [[Network interfaces, Instance IPs and DNS]]
- [[Placement Groups]]
- [[SSM parameter Store]]
- [[Scaling]]
- [[System and application logging]]
- [[Virtualization]]
- [[Launch Configuration (LC) & Launch templates (LT)]]

## Containers

- [[Containers & ECS & EKS]] — overview
- [[Introduction of Containers]]
- [[Elastic Container Registry (ECR)]]
- [[Elastic Container Service (ECS)]]
- [[Elastic Kubernetes service (EKS)]]

## Storage

- [[AWS S3]] — object storage
- [[Elastic File System (EFS)]] — POSIX file storage
- [[FSx]] — Windows / Lustre / NetApp file systems
- [[Storage Gateway]] — on-prem → AWS bridge
- [[AWS backup]]
- [[AWS Snowball]] — bulk physical data transfer
- [[AWS DataSync]] — online data transfer
- [[AWS Transfer Family]] — SFTP / FTPS / FTP

## Databases

- [[Relational Database Service (RDS)]] — managed relational DB
  - [[Type of database]]
  - [[RDS architecture]]
  - [[RDS - read replicas]]
  - [[RDS backup & restore]]
  - [[RDS data security]]
  - [[RDS proxy]]
  - [[Metrics]]
  - [[Aurora]]
  - [[ACID vs BASE]]
  - [[Run databases on EC2]]
- [[DynamoDB]] — managed NoSQL
  - [[Table & 2 types of backups]]
  - [[Operations, Consistency and Performance]]
  - [[Local & Global Secondary Indexes]]
  - [[Global Tables]]
  - [[Streams & Lambda Triggers]]
  - [[Accelerator (DAX)]]
  - [[TTL]]
  - [[VPC endpoint]]
- [[Elasticache]] — managed Redis / Memcached
- [[Redshift]] — data warehouse
- [[Database Migration Service (DMS)]]

## Networking

- [[VPC]] — virtual private cloud
- [[Route 53]] — DNS
  - [[DNS records types]]
  - [[DNSSEC]]
  - [[Routing Policies]]
  - [[Health checks]]
  - [[Public hosted zones]]
  - [[Private Hosted zones]]
  - [[Interoperability (work with 3rd party)]]
  - [[cname vs alias]]
- [[API gateway]]
- [[Cloudfront]] — global CDN
- [[AWS Global Accelerator]]
- [[AWS Direct Connect (DX)]]
- [[AWS Transit Gateway (TGW)]]
- [[AWS site-to-site VPN]]
- [[IPSec VPN fundamentals]]
- [[Border Gateway protocol (BGP)101]]

## Security, Identity & Compliance

- [[Identity Access Management (IAM)]]
  - [[IAM roles]]
  - [[AWS organization]]
- [[Cognito]] — application identity
- [[AWS Directory Service]]
- [[AWS Control Tower]]
- [[Key Management Service (KMS)]]
- [[CloudHSM]]
- [[AWS Certificate Manager (ACM)]]
- [[AWS Secrets Manager]]
- [[AWS Shield]]
- [[Web Application Firewall (WAF)]]
  - [[Firewalls (Layer 345 vs Layer 7)]]
- [[Amazon GuardDuty]]
- [[Amazon Inspector]]
- [[Amazon Macie]]

## Application Integration

- [[Simple Notification Service (SNS)]]
- [[AWS Simple queue service (SQS)]]
- [[Amazon MQ]]
- [[AWS EventBridge (Cloudwatch events)]]
- [[AWS Step functions]]
- [[Amazon Appflow]]

## Analytics

- [[Amazon Athena]]
- [[AWS Glue]]
- [[Kinesis]]
- [[AWS EMR]]
- [[AWS Opensearch Service]]
- [[Amazon DataZone]]
- [[Amazon Grafana]]
- [[Amazon Managed Workflows for Apache Airflow (MWAA)]]

## Machine Learning / AI

- [[Amazon SageMaker]]
- [[Amazon Comprehend]] — NLP
- [[Amazon Forecast]] — time-series
- [[Amazon Fraud Detector]]
- [[Amazon Kendra]] — enterprise search
- [[Amazon Lex]] — chatbots
- [[Amazon Polly]] — text → speech
- [[Amazon Rekognition]] — image / video
- [[Amazon Textract]] — OCR
- [[Amazon Transcribe]] — speech → text
- [[Amazon Translate]]

## Monitoring & Operations

- [[AWS Cloudwatch]]
- [[CloudWatch vs CloudTrail vs Config]]
- [[AWS Config]]
- [[AWS Cost Explorer]]
- [[AWS budgets]]
- [[AWS Application Discovery Service & Application Migration Service]]

## Infrastructure as Code & CI/CD

- [[CloudFormation]]
  - [[Terms]]
  - [[Parameters]]
  - [[Mapping]]
  - [[Output]]
  - [[Conditions]]
  - [[Intrinsic functions]]
  - [[DependsOn]]
  - [[DeletionPolicy]]
  - [[Change sets]]
  - [[Cross-Stack References]]
  - [[Nested Stacks]]
  - [[StackSets]]
  - [[Stack Roles]]
  - [[Custom resources]]
  - [[WaitCondition & Creation Policy]]
  - [[cfn-init]]
  - [[cfn-hup]]
- [[CICD in AWS]]

## See also

- [[_Azure_index|Azure]] — cloud counterpart
- [[_Terraform_index|Terraform]] — cloud-agnostic IaC
- [[_Data_Engineering_index|Data Engineering]] — concepts used in AWS data services
