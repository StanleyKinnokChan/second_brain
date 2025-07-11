# AWS EventBridge (Cloudwatch events)

- implement architecture when 
	- schedule: at Y times
	- Event pattern: X happens
	- Trigger: trigged by Z (e.g. Lambda, SQS, SNS)
- Cloudwatch events = stream events
- eventBridge is replacing Cloudwatch events
    - handle 3rd parties and custom action as well
- "event bus" is a stream of events (default only 1  and not visible), event bridge can have additional event buses
	- can be accessed by other AWS accounts using resource-based policies
		- events from another AWS account or regions
	- can archive events (all/ with filters) and send to an event bus
	- can replay archive events for bugs fixing
	- Eventbridge can inder the schema of events and let schma registry allows you to generate code for your application (can be versioned)
- eventBridge monitor the event bus with rule match incoming events/ schedules, the event could be routed to target (eg invoke Lambda function)
- resource-based policy

[[Cloudwatch events and eventBridge/Untitled.png]]
