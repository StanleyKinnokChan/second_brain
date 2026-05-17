---
title: AWS Serverless Application Model
tags:
  - aws
---

AWS Serverless Application Model

SAM = Serverless Application Model
- Framework for developing and deploying serverless applications
- All the configuration is YAML code
- Generate complex [[CloudFormation]] from simple SAM YAML file
- Supports anything from [[CloudFormation]]: Outputs, Mappings, Parameters, Resources…
- SAM can use CodeDeploy to deploy Lambda functions
- SAM can help you to run Lambda, API Gateway, [[DynamoDB]] locally

SAM Accelerate (sam sync)
- SAM Accelerate is a set of features to reduce latency while deploying resources to AWS
- sam sync
	- Synchronizes your project declared in SAM templates to AWS
	- Synchronizes code changes to AWS without updating infrastructure (uses service APIs & bypass [[CloudFormation]])