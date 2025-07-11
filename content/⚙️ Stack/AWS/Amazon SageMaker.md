# Amazon SageMaker

- fully managed machine learning service for whole data cycle
- fetch, clean, prepare, train, tune, evaluate, deploy, monitor
- data scientists and developers can quickly and easily build and train machine learning models (very niche)
- **Component**
    - **stage marker studio** - build, train, debug, monitor models (IDE for ML lifecycle)
    - **sagemarker Domain** - EFS volume, users, apps, policies, VPCs…isolation (grouping as a project)
    - **Containers** - prebuilt docker containers deployed to ML EC2 instance, providing a ML environments
    - **Hosting** - deploy endpoints for your ML model for other apps to utilize
- sagemaker itself has no cost, but resources inside it do


**SageMaker Feature Stores**
- A “feature” is just a property used to train a machine learning model
- Machine learning models require fast, secure access to feature data for training.
- It’s also a challenge to keep it organized and share features across different models
- It organizes the data in feature group within feature group
	- each features with records identifier, feature name, event name
- Online store (via PutRecord/ GetRecord API's from stream)
- Offline store in S3 (for batch)

**SageMaker ML Lineage Tracking**
- Creates & stores your ML workflow (MLOps)
- Keep a running history of your models
- Tracking for auditing and compliance
- Automatically or manually-created tracking entities
- Integrates with AWS Resource Access Manager for cross-account lineage
- Lineage Tracking Entities
	- Trial component (processing jobs, training jobs, transform jobs)
	- Trial (a model composed of trial components)
	- Experiment (a group of Trials for a given use case)
	- Context (logical grouping of entities)
	- Action (workflow step, model deployment
	- Artifact (Object or data, such as an S3 bucket or an image in ECR)
	- Association (connects entities together) – has optional AssociationType:
		- ContributedTo
		- AssociatedWith
		- DerivedFrom
		- Produced
		- SameAs
- Querying Lineage Entities
	- Use the LineageQuery API from Python
	- Do things like find all models / endpoints / etc. that use a given artifact
	- Produce a visualization

SageMaker Data Wrangler
- Visual interface (in SageMaker Studio) to prepare data for machine learning
- Import data
- Visualize data
- Transform data (300+ transformations to choose from)
- “Quick Model” to train your model with your data and measure its results
- feed into SageMaker Processing, SageMaker pipelines, Feature Store
- Produce code in notebook instead of be a part of pipeline
- Troubleshooting
	- Make sure your Studio user has appropriate IAM roles
	- Make sure permissions on your data sources allow Data Wrangler access
		- Add AmazonSageMakerFullAccess policy
	- EC2 instance limit
		- If you get “The following instance type is not available…” errors
		- May need to request a quota increase
		- Service Quotas / Amazon SageMaker / Studio KernelGateway Apps running on ml.m5.4xlarge instance