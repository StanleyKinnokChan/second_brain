---
title: 
tags:
  - Azure
---
**General storage (GPv2)**
**Subdivided into four types of data**

Azure Containers
- another name for blob storage
- folder-type structure metaphor for any type of file, no actual physical folder
- can change tier from hot to cold within a container
- can hold multiple containers (like bucket in AWS)

Azure file shares
- centralized service for everyone can storage files
- SMB standard for connect the file shares from multiple servers
- but for a common approach, company have their own file network and use file synchronization to azure instead

Azure Tables
- not like SQL DB, still a non-relational storage
- has URL to programmatically add stuff to the table
- use storage browser to add entity on fly to the table
- the entity properties can be not the same as previous one (semi-structure data)

Azure Queues
- place some message into a queue -> first in first out

**High Performance options**
- Premium SSD
- Premium SSD v2
- Ultra Disk