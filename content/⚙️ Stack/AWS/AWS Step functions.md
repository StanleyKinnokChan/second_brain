# AWS Step functions

<aside>
💡 **AWS Step Functions** is a visual workflow service that helps developers use AWS services to build distributed applications, automate processes, orchestrate microservices, and create data and machine learning (ML) pipelines.

</aside>

- workflow is called a state machine
- Each step in a workflow is a state
- Types of states
	- task: does sth with Lambda, other AWS services
	- Choice: Conditional logic
	- Wait: Delays state
	- Parallel: separate branches of execution
	- Map: run a set of steps for each item in a dataset
		- work with json, S3 objects, csv files
	- Pass, Succeed, Fail

- Advanced error handling and retry mechanism outside the code
- address limitation of lambda
    - 15 mins max execution time
    - gets messy at scale
    - cannot hold state (stateless)
- Step functions offer serverless workflow (start → states (things to occur)→ end)
- long running service (maximum duration of 1 year)
    - standard workflow for long time running
    - expression workflow for highly transactional
- started via API gateway, IOT rules, event bridge, lambda
- use **amazon states language**e (ASL) at control state in state machine- JSON template
- IAM role is used for permission

**state:**

- succeed & fail
- wait (until specific point)
- choice (take a path depending on condition)
- parallel (multiple choice needed)
- map (accept list of things and perform action for each thing)
- task (single unit of work, can be integrated by lambda, dynamoBD, ECS, SNS, SQS, glue…)
