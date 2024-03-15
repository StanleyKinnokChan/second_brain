# Accelerator (DAX)

<aside>
💡 **Amazon DynamoDB Accelerator (DAX)** is a fully managed, highly available, in-memory cache for Amazon DynamoDB that delivers up to a 10 times performance improvement—from milliseconds to microseconds—even at millions of requests per second.

</aside>

[[Accelerator (DAX]]%206c65f4f46559493db051082042950b47/Untitled.png)

- install DAX SDK in the application and it handles all the caches and data retrieval
- DAX caches data within VPCs
- less complexity without admin overhead - application no need to communicate with dynamoDB

**Architecture**

[[Accelerator (DAX]]%206c65f4f46559493db051082042950b47/Untitled%201.png)

- primary node (writes) & replicas (read)
- **in-memory cache** - great for scaling & speed
- **scale up** and **scale out** easily
- support **write-through**
- **DAX deployed** within a VPC, so application should be inside the VPC
