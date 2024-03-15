# Simple Notification Service (SNS)

[[Simple Notification Service (SNS]]%20ffeb4f28b96d423d80e15eb25f7b828f/Untitled.png)

- Public AWS service - requires network connectivity with public endpoint
- coordinates the sending and delivery of **messages (≤56KB payloads)**
- SNS topics are the base entity of SNS - **permission & configuration**
- **PUB SUB messaging**
    - publisher sends message to a TOPIC
    - TOPICS have **subscribers** which receive message
        - eg HTTP, Email, SQS, Mobile push, SMS
- offer
    - delivery status (HTTP, Lambda, SQS)
    - delivery retires
    - HA and sacalable
    - server side encryption (SSE)
    - cross-account via **TOPIC policy**
