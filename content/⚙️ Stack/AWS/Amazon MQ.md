# Amazon MQ

[[Amazon MQ/Untitled.png]]

- like a merge of SQS and SNS which both use AWS APIs, public services, AWS integrated
    - SQS provide queues (1:1)
    - SNS provide topic (1:many)
- if organization already use topics and queues on-premises and **want to migrate** to AWS, it play a role as a open-source message broker based on **Apache activeMQ**
- use JMS API
- provides queues and topics
- **VPC based & required private networking**
- no AWS native integration
