# Cloudwatch

[[Cloudwatch/Untitled.png]]

- public service - usable from AWS/ on-premises
- collects and manages operational data
- AWS integration - EC2, VPC, lambda, cloudtrail, R53…
- cloudwatch agent is needed to log data inside EC2
- can generate metrics based on logs

**3 Functions in one**

- **gathering/ collecting metrics** from AWS products, apps, on-premises
- **Logs** from AWS products, apps, on-premises
- **Events** - services (auto-scaling/ SNS) & schedules

**Concepts**

Namespace

- as a container for monitoring data
- format as AWS/’service’ (eg AWS/EC2)

Metric

- time ordered set of data points
- CPU usage
- Disk Reads and Writes
- Network IN and Out

Dimension

- separate the data from different perspectives (server/ instances)
- include instanceID, instancetype

Alarm

- link to metrics and flag the alarm state when certain metric condition is met, which may follow by an designated action

**Cloudtrail**

[[Cloudwatch/Untitled 1.png]]

- logs API actions which affect AWS account
- each log = cloudtrail event
- 90days stored by default in **event history**
- management events - for control plane operation
    - eg create, terminate EC2
- data events - resource operations
    - upload object to S3
- can be configured to one region/ all regions, global services (IAM,cloudfront) can be logged (need to be configured )
- can store the S3 as Json file (need to be configured)
- can be integrated with cloudwatch logs
- **Not realtime**
