# EC2 instance store

When an EC2 instance is launched, it is assigned ephemeral storage, typically labeled as ephemeral0, ephemeral1, etc. This storage is physically attached to the underlying host machine and is not network-attached like Amazon Elastic Block Store (EBS) volumes. Ephemeral storage is ideal for temporary data or cache, but it should not be relied upon for critical or persistent data.

The data on an instance store volume persists even if the instance is rebooted. However, the data does not persist if the instance is stopped, hibernated, or terminated. When the instance is stopped, hibernated, or terminated, every block of the instance store volume is cryptographically erased.
