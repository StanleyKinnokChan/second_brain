# Placement Groups

- influence close or not
- three type
    1. cluster - pack instances close together
        - launch all instance within a groups in a AZ, cannot span AW
        - fast direct bandwidth with single stream transfer rate with lowest latency possible
        - same rack, same time, same host
        - can span VPC peers
        - better to use the same type of instance/ at the same time
        - use cases: performance, fast speeds, low latency

        [[Placement Groups/Untitled.png]]

    2. spread - keep instances separated
        - spread across the AZ with distinct rack
        - provides infrastructure isolation, each instance runs from a different racks
        - each eack has its own network and power source
        - limit: 7 instances per AZ
        - use case: small number of critical instance that need to be kept separated from each other (eg domain controller/ file system)

        [[Placement Groups/Untitled 1.png]]

    3. partition - groups of instances spread apart
        - spread across the AZ with distinct rack
        - maximum of 7 partitions per AZ
        - in each partition you launch multiple instance
        - huge scale parallel computation but will have the resilience
        - great for topology aware application

        [[Placement Groups/Untitled 2.png]]
