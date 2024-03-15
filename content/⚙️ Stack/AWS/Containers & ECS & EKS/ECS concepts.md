# ECS concepts

On ECS host, you create a ECS cluster where you deploy the task , consisting of containers built by the images yourown or in ECR (AWS managed registry)

**Container definition** = (which image to use & which ports to expose)

**Task definition** = contained One or more container make up as a single application, store the resources used by the task (eg CPU/ memory), task role for security & resources

**Task role:** IAM role a task can assume, allow permission to use AWS resources

**Service definition:** how we want the task to scale (aka how many copies), load distribution, restarts…

[[ECS concepts/Untitled.png]]

**ECS cluster mode**

1. **EC2 mode**
    - Use EC2 as host within your VPC, need to manage them
    - need to worry about capacity and availability
    - host cost is needed
2. **Fargate mode**
    - don’t have to manage EC2, no service to manage
    - Host on a Fargate shared Infrastructure outside the VPC, where the task injected into VPC
    - Still be able to access inside or outside VPC with the IP
    - only pay for the container resources consumed


**ECS(EC2) vs ECCS(Fargate)**

[[ECS concepts/Untitled 1.png]]
