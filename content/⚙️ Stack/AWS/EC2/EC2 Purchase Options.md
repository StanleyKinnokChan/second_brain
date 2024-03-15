# EC2 Purchase Options

O**n-Demand**

- you rent a room, but you need to move to a new room every time you left
- per-second billing while it’s running
- other associated resource may charge externally
- No interruption capacity reservation/ upfront cost/ discount
- suitable for short-term workload/ uncertainty

**Spot**

- you rent the left-over room, if they need it, you kick out until they left
- selling the spare capacity in the host
- spot price > your maximum price, your instances terminate
- very cheap (90% cheaper) if you can be interrupted
- Never use spot for workloads which can’t tolerate **interruptions**
- anything is stateless

**Standard Reserved**

- you commit that you will use the resources for a length of time, in exchange with a cheaper price = subscription
- For long term consistent usage (1/3 yrs)
- you will pay for the reservation if you use the resource
- more upfront you pay, cheaper the free per second

**Schedule Reserved instances**

- specify the time-span you will used
- eg you only needs a computing something every weekend for certain number of hours recursively

**Capacity reservation**

- just for the capacity where you cannot justify a long-term commitment

**Dedicated Hosts**

- you rent the whole building
- pay for the host itself that come with all the resources and machine, no instance charges
- physical server isolation
- host affinity = links instances to hosts = remain on same host even stop & start ⇒ licensing implication
- you can use the sockets/ cores of the machine you pay with the licensing requirement
- capacity management required
- with AMI limits and not support RDS/ placement group

**Dedicated instances**

- you rent a room, always stay in this room
- You don’t own, or share the host
- physically isolated at the host hardware level from instances that belong to other AWS accounts
- keep that part of physical intra-structure is for your own use

**Saving plan**

- hourly commitment for a 1/3 year term
- **2 type of resevations**
    1. reservation of general compute $ amounts
    2. specific EC2 savings Plan - flexibility on size & OS (also for fargate/ Lambda)
- commit the minimum spend on all these services with saving plan, discount if the commitment is achieved
