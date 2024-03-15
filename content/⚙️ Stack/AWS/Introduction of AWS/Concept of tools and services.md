# Concept of tools and services

- **Elastic Load Balancing** automatically distributes traffic across multiple EC2 instances, which helps achieve better fault tolerance and availability. It performed health checks for the resources and only sends the request to the healthy one

- Storage Services:
    - a reliable, scalable, and secure place for data
    - Elastic Block Store
        - like a hard drive for EC2 instance
        - an instance can connect to one or multiple blocks
    - S3
        - bulk object storage service for the internet that is designed to make web-scale computing easier
        - store data as objects in resources called buckets
        - use cases:
            - data lakes from structured or unstructured data
            - backup and storage
            - application/media hosting
            - software delivery
        - storage class

            [[Concept of tools and services/Untitled.png]]

            - more infrequent access and cheaper the price
    - S3 Glacier
        - data achieve and backup
    - Storage Gateway

        integrate cloud storage with on-site workloads between organization’s on-premises IT env. and AWS storage infrastructure

    - Elastic File system

        file storage service for creating and configuring file system

    - FSx
- Database services
    - offload time-consuming management task, reduce undifferentiated heavy lifting, provide automatic backup/recovery
    - RDS
        - relational database
    - DynamoDB
        - NoSQL database
    - ElastiCache
        - fast caching system

- Networking services
    - Isolate cloud infrastructure
    - VPC
        - build a virtual network in the cloud
        - advance security features: access control lists and security groups
        - create subnet and range of IP address
        - flow logs: capture network flow information
    - security groups
        - Virtual firewall at the subnet level
    - Network Access Control Lists (NACL)
        - Virtual firewall at the instance level
    - Route 53
        - route end users to internet applications by translating human readable name to numeric IP address

- Security
