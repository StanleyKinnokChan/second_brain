# Simple queue service (SQS)

**Overall**

- manage public, fully managed, HA message queue
- message up to (256KB in size), link to large data in S3 if size exceeds the limit
- the message being pulled are hidden (VisibilityTimeout) for a time (allow fault tolerant)
    - client deleted → message gone
    - client ignore → message reappear after timeout
- **ASGs can scale and lambdas invoked based on queue length**
- supports server-side encryption at rest (KMS) & in-transit
- queue policy (like a resource policy) allow access from external account
- allow **FANOUT architecture**, there the a object undergoes different process to generate different output

[[Simple queue service (SQS]]%20cf2446933fdc416886d67fa963b712f5/Untitled.png)

**Two type of queue**

[[Simple queue service (SQS]]%20cf2446933fdc416886d67fa963b712f5/Untitled%201.png)

1. **standard** (at-least-once; order is not guaranteed)
    - faster and occasionlly produce 1 more copy of message
    - good for decoupling, worker pools processing
2. **FIFO** (exactly-once;  order is guaranteed)
    - 3,000 message/s with batching, or up to 300 message/s without
    - billed based on ‘requests’ (1requrest = 1-10messages up to 64KB)
    - with **.fifo suffix**
    - great for sequential command

**Two way to poll queues**

- **short**: immediate poll, 1 request is counted even there are 0 messages
- **long**: preferred one, wait until message arrived with specified wait time (waitTimeSeconds)

**Delay Queues**

- allow postpone the message being visible from queue (bottom case) when first being added to the queue
- good for supporting the application that needs pre-processing/ actions beforehand before the execution of the message

[[Simple queue service (SQS]]%20cf2446933fdc416886d67fa963b712f5/Untitled%202.png)

**Dead-letter Queues**

- can be used for problem/reoccurring failure messages, carrying out different set of processing
- message is dropped after retention day (normally only 1 day more than normal queue)

[[Simple queue service (SQS]]%20cf2446933fdc416886d67fa963b712f5/Untitled%203.png)
