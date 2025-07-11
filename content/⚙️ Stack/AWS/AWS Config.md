# AWS Config

- Helps with auditing and recording compliance of your AWS resources (Pay-service)
- track and auditing **changes over time** on acc resources, compliance with standards
- Does **not prevent changes happening** itself !!
- **regional service**, but also supports **cross-region** & **account** aggregation
- can generate SNS notifications and near-realtime event via EventBridge & Lambda if the configuration deviation from the compliance (evaluated against **config rules**)
- Possibility of storing the configuration data into S3 (analyzed by Athena)

**Questions that can be solved by AWS Config:**
- Is there unrestricted SSH access to my security groups?
- Do my buckets have any public access?
- How has my ALB configuration changed over time?

**Config Rules**
- Can use AWS managed config rules (over 75)
- Can make custom config rules (must be defined in AWS Lambda)
	- Ex: evaluate if each EBS disk is of type gp2
	- Ex: evaluate if each EC2 instance is t2.micro
- Rules can be evaluated / triggered:
	- For each config change
	- And / or: at regular time intervals

**AWS Config Resource**
- View compliance of a resource over time
- View configuration of a resource over time
- View CloudTrail API calls of a resource over time

**Config Rules – Remediations**
- using SSM Automation Documents to trigger the Auto-Remediation Action
- can create custom Automation Documents that invokes Lambda function
- can set Remediation Retries if the resource is still non-compliant after auto-remediation

**Config Rules – Notifications**
- Use EventBridge to trigger notifications when AWS resources are non-compliant
- Ability to send configuration changes and compliance state notifications to SNS (all events – use SNS Filtering or filter at client-side)
