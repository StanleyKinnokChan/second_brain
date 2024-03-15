# AWS Local Zones

**AWS w/o local zone**

[[AWS Local Zones/Untitled.png]]

**AWS w/ local zone**

- multiple smaller local zone spreading in the city with their own infrastructure (no built in resilience)
- the subnet can be extended to these local zone and use the resources as usually as in parent region, but with much lower latency
- support **DX connect** to a local zone
- local zone has the private connectivity with the parent region
- the resources like **S3/ EBS snapshots will be taken to parent region**, which still benefited from the HA provided
- However, **not all products support** local zones

[[AWS Local Zones/Untitled 1.png]]
