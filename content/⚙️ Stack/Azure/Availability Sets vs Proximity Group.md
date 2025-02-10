---
title: 
tags:
  - Azure
---
### Availability Sets
When you have multiple VMs that have an identical function, but you want them to be separate from each other for fault isolation purpose
- seperate power sources & network
- updates one at a time

### Proximity Group 
When you have multiple VMs that have an identical function, but you want them to be placed close together (e.g. same rack) for more performance and fast inter-server communication.
- arranged in a VM scale set
![[Pasted image 20250104123029.png]]