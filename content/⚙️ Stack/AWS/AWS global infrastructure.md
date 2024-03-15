# AWS global infrastructure

**Global component:**

- global service location & discovery (global DNS & routing)
- content delivery network and optimisation (content is cached locally, as close the customers as possible with cloudfront)
- global health checks & failover

**Regional component**

[[AWS global infrastructure/Untitled.png]]

- regional entry point (VPC/ AWS public zone/APIs/ load balancer)
- scaling & resilience
- application services and components

edge location = distribution point where the end user can access the catched data

direct connect: build your own optimized connection to data center

- direct connect location: trusted partnered data centre (may not be AWS)
