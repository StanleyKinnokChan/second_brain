---
title: AWS Global Accelerator
tags:
  - aws
---

# AWS Global Accelerator

- start with 2x **anycast IP** address, all global accelerator edge location have all using this pair of IPs
- user pointing the IPs will be routed to the closest global accelerator edge location, then data transits globally across the **AWS global backbone network** fully control by AWS
- don’t cache data like cloudfront, it accelerate the data transit from client to the location of the target infrastructure
- can be used for NON HTTP/S (e. g. TCP/UCP)

## Disaster Recovery

- Global Accelerator performs **health checks** for the application
- **Failover in less than 1 minute** for unhealthy endpoints

<aside>
💡 Anycast IP address **allows multiple servers to share the same IP address**, allowing for multiple physical destination servers to be logically identified by a single IP address.

</aside>
