# Step functions

<aside>
💡 **AWS Step Functions** is a visual workflow service that helps developers use AWS services to build distributed applications, automate processes, orchestrate microservices, and create data and machine learning (ML) pipelines.

</aside>

[[Step functions/Untitled.png]]

- address limitation of lambda
    - 15 mins max execution time
    - gets messy at scale
    - cannot hold state (stateless)
- Step functions offer serverless workflow (start → states (things to occur)→ end)
- long running service (maximum duration of 1 year)
    - standard workflow for long time running
    - expression workflow for highly transactional
- started via API gateway, IOT rules, eventbridge, lambda
- use **amazon states languag**e (ASL) at control state in state machine- JSON template
- IAM role is used for permission

**state:**

- succeed & fail
- wait (until specific point)
- choice (take a path depending on condition)
- parallel (multiple choice needed)
- map (accept list of things and perform action for each thing)
- task (single unit of work, can be integrated by lambda, dynamoBD, ECS, SNS, SQS, glue…)
