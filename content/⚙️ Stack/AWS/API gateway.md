# API gateway

<aside>
💡 Amazon ***API Gateway*** is a fully managed service that makes it easy for developers to create, publish, maintain, monitor, and secure APIs at any scale.

</aside>

[[API gateway/Untitled.png]]

- sits between applications & integrations
- HA and scalable, handles authorisation, throttling, OpenAPI, direct integration
- can connect to services/ endpoints in AWS or on-premise
- support HTTP, REST, WebSocket APIs

**Authentication:**

[[API gateway/Untitled 1.png]]

**Endpoints type**

- edge-optimized - routed to the nearest Cloudfront POP
- Regional - client in the same region
- private - only accessible only within a VPC via interface endpoint

**Stages**

- A stage is a named reference to a deployment, specific lifecycle stage or version of your API
- each stage has its o**wn endpoint URL and own settings**, which can be deployed individually
- provide isolation and testing
- stages enable for **canary deployment** (splits traffic between an already-deployed version and a new version, rolling it out to a subset of users before rolling out fully.)
- The canary can be promoted to make it the new base ‘stages’

[[API gateway/Untitled 2.png]]

**Errors**

[[API gateway/Untitled 3.png]]

**Caching**

[[API gateway/Untitled 4.png]]
