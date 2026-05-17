---
title: Join hint
tags:
  - spark
---
[[Spark]] approaches cluster communication in two different ways during joins. It either incurs (1) a **shuffle join**, which results in an all-to-all communication or (1) a **broadcast join**.

#### Shuffle Join
- for both big tables with partition
- every node talks to every other node and they share data according to which node has a certain key or set of keys (on which you are joining)
- these joins are expensive because the network can become congested with traffic, especially if your data is not partitioned well.
#### Broadcast Join
- for big tables joining with small table
- given that the small table fit in a worker node, it is replicated onto every worker node in the cluster to join each partition
- without having to wait or communicate with any other worker node, joins will be performed on every single node individually
- first step is expensive
- if you try to broadcast something too large, you can crash your driver node