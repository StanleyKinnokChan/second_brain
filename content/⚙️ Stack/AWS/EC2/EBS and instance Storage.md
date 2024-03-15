# EBS and instance Storage

- **Storage performance**
    - IO (block) size per read/write * IOPS (how many read/write can handle per second) = throughput (XX MB/s)
        - **Storage type**

            **Block storage**

            - volumn presented to OS as a collection blocks
            - no structure provided (no sth like foldcer-file like hierarchy)
            - Mountable & bootable
            - EBS

            **File storage**

            - presented as a file share.. has structure
            - Mountable & not bootable
            - use when you want to share

            **Object storage**

            - collection of objects with key and value
            - flat
            - not mountable & not bootable
            - super-scalable
            - good for read & write
    - can be capped with storage/ system limitation
    - the bucket fills by baseline performance

**Two way**

- direct (local) attached storage
    - storage on the EC2 host
    - ephemeral storage - temporary
- network attached storage
    - volume delivered over the networks (EBS)
    - Persistent storage - lives on past the lifetime of the instance

- EBS volume type
- **Solid state drives (SSD) (gp2 and io1 and io2):**
    - For **transactional workloads involving frequent read/write operations with small I/O size**.
    - Dominant performance attribute is **IOPS**.

    [[EBS and instance Storage/Untitled.png]]

- **Hard disk drives (HDD) (st1 and sc1):**
    - For **large streaming workloads**.
    - Dominant performance attribute is **throughput**.
    - **Can't be used for boot volumes**

    [[EBS and instance Storage/Untitled 1.png]]


- **Instance store volume**
    - block storage devices
    - local on EC2 host
    - physically connected to 1 EC2 host
    - list on instance move, resize  or hardware failure
    - instances on that host can access them
    - highest storage performance and included in instance price
    - have to attached at launched, cannot attach them afterward if not
    - highest performance (very high IOPS/ thoughtput)
    - **temporary - don’t use for persistence data storage**

- **Choice between Instance store volume & EBS**
    - EBS
        - persistence
        - resilience
        - storage isolation
    - Depends
        - resilience w/ app in-built replication
        - high performance need
    - Instance store
        - cheap
        - super high performance
    - **Quick decision**

        cheap EBS = ST1 or SC1

        throughput & streaming = ST1

        BOOT = not ST1. SC1

        GP2/3 = up to 16,000 IOPS

        IO1/2 = up to 64,000 IOPS (256,000 for block express)

        RAID0 + EBS up to 260,000 IOPS (max of instance)

        instance store for > 260,000 IOPS for non-persistent data


- **EBS snapshot**
    - copies to S3 (⇧resilience) as backup
    - first is a full copy of data on the volume, future snaps are incremental
    - volume can be created from snapshot, can be copied to another region/ other AZs

    [[EBS and instance Storage/Untitled 2.png]]

    - performance
        - new EBS volume = full performance immediately
        - volume restore lazily from snaps and take time if no request was made
        - Requested data from S3 are fetched immediately but in a low performance
        - force a read of all data immediately using some admin procedure
        - but fast snapshot restore (FSR) allows an immediate restore , but cost $
    - billing
        - pay by Gigabyte-month, only for changed volume is used
        - incremental for the changes being made
- EBS Encryption
    - EBS can use KMS key to generate data encryption key (DEK), load into EC2 to encrypt the data than transfer to EBS
    - snapshot is also encrypted correspondingly
    - accounts can be set to encrypt by default or customized
    - each volume uses 1 unique DEK, same DEK is used for decrypting snapshots & future volumes
