# AWS Cloudwatch

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

### **Concepts**

**Namespace**
- as a container for monitoring data
- format as AWS/’service’ (eg AWS/EC2)

**Dimension**
- separate the data from different perspectives (server/ instances)
- include instanceID, instancetype

**Metric**
- provides metrics for every services in AWS, belong to a namespaces
- have timestamps
- up to 30 dimensions per metrics
- can create custom metrics (e.g. extract RAM usage via unified agent on EC2 instance/ on-premise servers)
- metrics streams:
	- to kinesis
	- to 3rd party service, S3, amazon via firehose
	- option to filter metrics to only stream a subset of streams

**Logs**
- store application log
- log groups: abitrary name representing an application
- log stream: instances within application/ log files/ containers
- log expiration policies: can be defined as never expire, 1d to 10y...
- send to S3, kinesis, lambda
- logs are encrypted by default
- metrics filter to create metrics from logs
- sources
	- SDK, Cloudwatch logs agent, unified agent
	- Elastic beanstalk
	- ECS: from containers
	- AWS Lambda collection from function logs
	- VPC flow logs
	- API gateway
	- cloudtrail
	- route53: DNS queries
- Queries and analyze log by CloudWatch Logs Insights
	- able to filter, agg, sort and limit
- Export
	- can export to S3 (via CreateExportTask API, non Realtime)
	- can export to kinesis/ Lambda (via Logs subscriptions, Realtime and multiple account is possible by cross-account subscription)

**Alarm**
- link to metrics and flag the alarm state when certain metric condition is met, which may follow by an designated action
- State (OK, insufficient_data, alarm)
- Period (length of time (s) to evaluate metrics)
- can based on CloudWatch logs metrics filters
- can manually trigger alarm in CLI
- Targets:
	- Stop, Terminate, Reboot, or Recover an EC2 Instance
	- Trigger Auto Scaling Action
	- Send notification to SNS (from which you can do pretty much anything)s
- Composite Alarms
	- monitoring the states of multiple other alarms (with and/or condition)
	- reduce “alarm noise” by creating complex composite alarms
- EC2 instance recovery
	- Status check:
		- instance status
		- system status (hardware)
		- attached EBS status
	- Recovery: Same Private, Public, Elastic IP, metadata, placement group

**CloudTrail**
- Provides governance, compliance and audit for your AWS Account (enabled by default!)
- Get an log (history of events / API calls) made within your AWS Account by:
	- Console
	- SDK
	- CLI
	- AWS Services
- Can put logs from CloudTrail into CloudWatch Logs or S3
- Can be configured to one region/ all regions, global services (IAM, cloudfront) can be logged (need to be configured)
- e.g. who deleted the EC2?? -> check CloudTrail
- 90days stored by default (for longer retention, use S3 & Athena as Json)
- Event type
	- Management events - for control plane operation
		- Operations that are performed on resources in your AWS account
		- Can separate **Read Events** (that don’t modify resources) from **Write Events** (that may modify resources)
	    - e.g. create, terminate EC2
	- Data events - resource operations
		- can separate read and writes event
	    - upload object to S3, Lambda function via Invoke API
	- CloudTrail Insight events (pay-service)
		- analyzes normal management events to create a baseline
		- then detect unusual activity in your account via analyzing write events:
			- inaccurate resource provisioning
			- hitting service limits
			- Bursts of AWS IAM actions
			- Gaps in periodic maintenance activity
- can be integrated with CloudWatch logs
- Not Realtime

**CloudTrail Lake**
- Managed data lake for CloudTrail events
- Integrates collection, storage, preparation, and optimization for analysis & query
	- Events are converted to ORC format
- Enables querying CloudTrail data with SQL
- Enable it with the “Create event data store” menu choice in the console
- Data is retained for up to 7 years
- Specify the event types you want to track (Management events/ Data events)
- Note KMS events add up fast and can make your costs blow up
- Basic event selectors can be selected in the UI
- Finer grained selection may be achieved with advanced event selectors
	- What fields, what prefixes, event type, resources, event name....
	- This can help control your ingestion and storage costs
- You can create “channels” to integrate with events outside of AWS
	- Built-in support for Okta, LaunchDarkly, Clumio, and other CloudTrail partners
	- Or custom integrations
- Querying 
	- Lake dashboards allow you to visualize events
	- Roll your own SQL queries
	- Start from sample queries in the CloudTrail Lake Editor
	- Remember to bound your queries by eventTime to constrain costs

