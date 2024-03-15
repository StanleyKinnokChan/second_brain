# High-Availability vs Fault-Tolerance vs Disaster Recover

**High-Availability**

- when it fail, its component can replace as soon as possible
- = maximize the online time of a service/uptime = minimize downtime
- measure by available time (e.g. 99.999% = 5.26 minute/ year downtime)
- allow interuption

**Fault-Tolerance**

- more than high-availability
- it is a property that enables a system to continue operating properly in the event of the failure of some of its components
- actively connected to multiple servers
- minimize interruption occur even with failure
- can cost much more

**Disaster Recover**

- a set of policies, tools and procedures to **enable the recovery or continuation of vital technology infrastructure & systems** following a natural or human-induced disaster
- pre-planning + (automated) DR process
- back-up plan when disaster
- multiple site of backups
