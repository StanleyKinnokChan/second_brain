# Cloudwatch events and eventBridge

- implement architecture when X happens/ at Y times
- Cloudwatch events = stream events
- eventBridge is replacing Cloudwatch events
    - handle 3rd parties and custom action as well
- event bus is a stream of events (default only 1  and not visible), eventbridge can have additional event buses
- eventBridge monitor the event bus with rule match incoming events/ schedules, the event could be routed to target (eg invoke Lambda function)

[[Cloudwatch events and eventBridge/Untitled.png]]
