---
title: 
tags:
  - Snowflake
---
By default, a virtual warehouse consists of a single cluster of compute resources available to the warehouse for executing queries. As queries are submitted to a warehouse, the warehouse allocates resources to each query and begins executing the queries. 

If sufficient resources are not available to execute all the queries submitted to the warehouse, Snowflake queues the additional queries until the necessary resources become available.

#### Two modes:
**Maximized: **
- enabled by specifying the same value for both maximum and minimum number of clusters
- when the warehouse is started, Snowflake starts all the clusters so that maximum resources are available while the warehouse is running.
- effective for statically controlling the available compute resources
**Auto-scale:**
- enabled by specifying different values for maximum and minimum number of clusters
- Auto-scaling depends on workloads


##### Scaling Policy
- help control the credits consumed by a multi-cluster warehouse running in Auto-scale mode
- determine how to adjust the capacity of your multi-cluster warehouse by starting or shutting down individual clusters while the warehouse is running
- Two policies:
	1. Standard: 
		- Favors prevention of queuing
		- warehouse starts immediately when query is queued
		- 2-3 checks per min to see if loads from least loaded warehouse can be distributed to other and shut it down
	2. Economy:
		- Favors conserving credit
		- Estimates query load enough to keep new warehouse busy for at least 6 minutes
		- 5-6 checks per min to see if loads from least loaded warehouse can be distributed to other and shut it down