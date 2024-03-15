# Architecture Design

Avoid

[[Architecture Design/Untitled.png]]

Tiered Architecture

[[Architecture Design/Untitled 1.png]]

- Each Tier same/different server → allow vertical scale
- with load balancer, the instance that are communicating are not specific (abstracted) ⇒ allow horizontal scaling
- 2 problems:
    - tiers are still couple → upload expects and requires processing to respond → upload is fail = whole system is fail
    - each tier has to be running sth for app even there are nothing to run → processing tier keep asking


Queue-based (decoupled tier)

[[Architecture Design/Untitled 2.png]]

- instead of directly deliver to processing tier, it stores in S3 and add message to queue
- processing auto-scaling based on queue length
    - no message = no processor
    - many message = many processor


**Microservice architecture**

- If there are a lot of service breaking down from monolithic one, it can be very complicated with queue based architecture

[[Architecture Design/Untitled 3.png]]

**Event Driven architecture**

- a collection of event producer and consumers
- Event producer produce event in response to some actions, event consumers reacts to event
- They are not consuming resource if no specific action happen.  **No constant running/ waiting**
- **Event router** manage lots of event, event to event router and deliver to event consumer
- Mature event-driven architecture **only consumes resources while handing events** (serverless)

[[Architecture Design/Untitled 4.png]]

**Serverless architecture**

- serverless isn’t one single thing
- you manage few, if any servers - low overhead
- application are a **collection of small & specialised functions**
- stateless and ephemeral env. - only billing the duration
- **FaaS** & **managed service** is used when possible for compute functionality, e.g.:

[[Architecture Design/Untitled 5.png]]
