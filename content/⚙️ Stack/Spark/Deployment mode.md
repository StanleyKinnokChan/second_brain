---
title: Deployment mode
tags:
  - spark
  - exam
---
# 1. Client Mode

In client mode, the [[Spark]] driver runs within the client process instead of the master node, which is typically the machine from which you submit your [[Spark]] application. The client communicates directly with the cluster manager (e.g., YARN, Mesos, or Spark Standalone) to request resources and execute tasks.

✅  This mode is used by spark-shell, notebooks interactively, yet a dependency is generated between the client and the cluster. If the client suffers any damage or shuts down, the driver dies, and the executors assigned to the driver are orphaned, and so the Resource Manager terminates the process. Normally used in testing/ development

# Key Characteristics:

- Driver runs on the client machine.
- Want to get a job result (dynamic analysis)
- Control where your Driver Program is running
- Client machine requires access to the Spark cluster’s configuration.
- Well-suited for interactive or development environments.


# 2. Cluster Mode

In cluster mode, the Spark driver runs on one of the cluster nodes rather than on the client machine. The client submits the Spark application to the cluster manager, which launches the driver within one of its worker nodes. 

✅ Once the spark-submit is done, we can disconnect from our client machine, and the latency time between the driver and the executor is minimal. In production environments we should always choose to use Cluster Mode.
# Key Characteristics:

- Driver runs on one of the cluster’s worker nodes.
- Client machine does not need to maintain an active connection to the cluster during application execution.
- Recommended for production deployments.