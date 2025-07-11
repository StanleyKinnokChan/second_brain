---
title: 
tags:
---
3 types of network:
- container to internet (default)
- container to local host (use host.doc ker.internal as address)
- container to container 
	- hardcode: the ip address of another container can be found via `docker inspect <container_id>`), which can be used in the primary container
	- To allow multiple containers talk to each other, we need a **container networks**


```
docker network create my_network     # create a docker interal network
docker run --network my_network ...  # run container with the networ
```
- create a network shared by multiple containers
- IPs are automatically resolved by using the service name (e.g. mongodb://172.17.0.2:27017 -> mongodb://mongodb_container:27017 )
- docker WILL NOT replace the resource, it just detects the outgoing requests and resolves the IP for such requests