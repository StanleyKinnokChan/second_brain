# Elastic Container Service (ECS)

Launch Docker containers on AWS = Launch ECS Tasks on ECS Clusters

On ECS host, you create a ECS cluster where you deploy the task , consisting of containers built by the images your own or in ECR (AWS managed registry)

**Container definition** = (which image to use & which ports to expose)

**Task definition** = contained One or more container make up as a single application, store the resources used by the task (eg CPU/ memory), task role for security & resources

**Task role:** IAM role a task can assume, allow permission to use AWS resources

**Service definition:** how we want the task to scale (aka how many copies), load distribution, restarts…

[[ECS concepts/Untitled.png]]

**ECS launch type**

1. **EC2 mode** 
    - Use EC2 as host within your VPC, need to manage them
    - ECS agent is put into EC2 to allow the control of containers
    - need to worry about capacity and availability
    - host cost is needed
2. **Fargate mode**
    - don’t have to manage EC2, no service to manage (serverless)
    - just create task definitions
    - Host on a Fargate shared Infrastructure outside the VPC, where the task injected into VPC
    - Still be able to access inside or outside VPC with the IP
    - only pay for the container resources consumed


IAM roles for ECS
- EC2 Instance Profile (EC2 Launch Type only:
- Used by the ECS agent
- Makes API calls to ECS service
- Pull Docker image from ECR
- Reference sensitive data in Secrets Manager or SSM Parameter Store
ECS Task Role:
- Allows each task to have a specific role
- Use different roles for the different ECS Services you run
- Task Role is defined in the task definition

Load Balancer Integrations
- if a user need to access ECS
- Application Load Balancer - supported and works for most use cases
- Network Load Balancer - recommended only for high throughput / high performance use cases, or to pair it with AWS Private Link

Data Volumes (EFS)
- Mount EFS file systems onto ECS tasks
- Works for both EC2 and Fargate launch types
- Tasks running in any AZ will share the same data in the EFS file system
- Use cases: persistent multi-AZ shared storage for your containers
- Amazon S3 cannot be mounted as a file system