# Amazon SageMaker

- fully managed machine learning service for whole data cycle
- fetch, clean, prepare, train, evaluate, deploy, monitor
- data scientists and developers cwan quickly and easily build and train machine learning models (very niche)
- **Component**
    - **stage marker studio** - build, train, debug, monitor models (IDE for ML lifecycle)
    - **sagemarker Domain** - EFS volume, users, apps, policies, VPCs…isolation (grouping as a project)
    - **Containers** - prebuilt docker containers deployed to ML EC2 instance, providing a ML environments
    - **Hosting** - deploy endpoints for your ML model for other apps to utilize
- sagemaker itself has no cost, but resources inside it do
