# API gateway


fully managed service that makes it easy for developers to create, publish, maintain, monitor, and secure APIs at any scale.


- Allow an exposure of your application to public and also acts as a front door with a of features
- sits between applications & integrations
- handle API versioning, different environment, security, authorization, throttling, OpenAPI, direct integration
- transform and validate requests and response
- Cache API responses
- can connect to services/ endpoints in AWS or on-premise
- support HTTP, REST, WebSocket APIs


Integration:
- invoke lambda function
- HTTP
	- expose HTTP endpoints in the backend
	- allow rate limiting, cahing, API keys...
- AWS service
	- e.g. AWS steps functions, post a message to SQS
	- why? Add authentication, deploy plublicly, rate control

**Authentication:**


Endpoints type

- edge-optimized - routed to the nearest Cloudfront edge locations (API gateway still lives in only one regions)
- Regional - client within the same region (more contol over cahing strategies)
- private - only accessible only within a VPC via interface endpoint (ENI)

Security:
- User Authentication through
	- IAM roles (internal applications)
	- Cognito (external)
	- Custom Authorizer with lambda
- Custom Domain Name HTTPS security through integration with **AWS Certificate Manager**
	- must setup CNAME or A-alias record in Route 53

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
