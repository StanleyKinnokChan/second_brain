# System and application logging

- cloudwatch is for metrics, and cloudwatch log is for logging
- neither natively capture data inside an instance
- cloudwatch agent is required to capture OS visible data
    - cloudwatch agent can be downloaded
    - configuration and permissions (IAM role) are needed
    - the capture data can send to cloud watch logs
- cloudformation can help to configuration and SSM parameter store can save the log-in info
