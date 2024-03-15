# Auto Scaling Group

[Launch Configuration (LC) & Launch templates (LT)](Auto%20Scaling%20Group%20f84c189701e94e23b8af74709df801f6/Launch%20Configuration%20(LC)%20&%20Launch%20templates%20(LT)%204865bfbcf075410e8650b67826bf84d3.md)

- auto-scaling and self-healing for EC2
- self-healing - create an instance and terminate old problematic one
- ASG defines **When & where**, uses LT/ LC defines **what**
- fee and only the resources created are billed
- more effective for **more and smaller** instances
- Three important value
    - minimum, Desired & maximum (eg 1:2:4)
- keep running instances at the desired capacity by provisioning/ terminating instances
- **scaling policies** automate based on metrics (eg CPU)
    - rule that adjust the values of Auto Scaling Group
    - AGEs can have no scaling policies
    - 4 scaling method:
        - **simple scaling** - manually adjust the desired capacity
        - **scheduled scaling** - time based adjustment - e.g. sales
        - **dy**namic scaling
            - simple ‘CPU above 50% +1’/ ‘CPU below 50% -1’
            - **stepped scaling** - multiple range +1/-1
            - **target tracking** - set a desired aggregated metric (40% CPU on avg)
            - scale based on SQS - based on number of messages
- cooldown periods exists for next scaling

**Scaling processes**

- **Launch** & **terminate** - suspend & resume
    - Launch=suspend: won’t scale out if any alarms / schedule take place
    - terminate =suspend: won’t terminate instances
- **AddToLoadBalancer** - add to LB on launch
- **AlarmNotification** - accept notification from cloudwatch
- **AZRebalance** - balances instances evenly across all of the AZs
- **HealthCheck** - instance health checks on/ off
- **ReplaceUnhealthy** - terminate unhealthy and replace
- **scheduledActions** - scheduled on/off
- **Standby** - use this for instances ‘inService vs Standby’

**Lifecycle Hooks**

[[Auto Scaling Group/Untitled.png]]

- allow **custom actions** on instances during ASG action during instance launch/ terminate transition
- instances are paused within the flow - wait until a timeout then either **continue/ abandon**
- Closely work with EventBridge/ SNS

**Health Checks**

- EC2 (default), ELB (can be enabled) & custom
- EC2 - can be more application aware
    - Unhealthy = stopping, stopped, terminated, shutting down or impaired
    - healthy = running & passing ELB health check
- Custom - by an external system
- health check grace period (default 300s) - delay before starting checks
- allow system launch, bootstrapping and application start
