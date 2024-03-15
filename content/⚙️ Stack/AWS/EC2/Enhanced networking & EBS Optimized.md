# Enhanced networking & EBS Optimized

**Enhanced networking**

- the origin host didn’t recognize virtualization. The networking interface has to deal with instance one by one
- use SR-IOV for Network Functions Virtualization,  to improve the overall performance of EC2 networking for free
- create logical network interface for each instances
- provides higher IO/ more bandwidth, lower host CPU usage, higher packets-per-second (PPS), low latency

**EBS Optimized**

- EBS = block storage deliver over network (shared for both data and EBS)
- EBS optimized means dedicated capacity for EBS (separated out the storage)
- most instances support and have enable by default
- some support, but enabling costs extra
