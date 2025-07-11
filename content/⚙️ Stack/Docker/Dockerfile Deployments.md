---
title: 
tags:
---
Watch-outs
- bind mount shouldn't be used in production
- containerized apps might need a build step
- multiple-containers projects might need to be split across multiple hosts
- trade-offs between control and responsibility might be worth it

### Options 1 - manual way
Deployment Process:
- develop application
- add dockerignore, tag the container with the name in dockerhub
- push image to a container registry (e.g. dockerhub)
	- e.g. docker login & docker push
- install docker on a remote host (e.g. via ssh)
- pull image from the container registry on a remote host
- run container based on image on remote host

Updates container:
- build and push the new image to the registry locally
- Remote pull and re-run on remote host

Downside:
- Management of network, security groups/ firewall

### Options 2 - managed services (ECS)
Deployment Process:
- develop application
- add dockerignore, tag the container with the name in dockerhub
- push image to a container registry (e.g. dockerhub)
	- e.g. docker login & docker push
- reference the image in the managed provider, enter the info for env var, ports, volume, which then pull image, and build and run container automatically

*The ip resolution in the application won't work anymore as it is a docker functionality. Use env variable to define the ip address
*for multiple-container app, you have to pre-build all images and run them on a task/ cluster

Updates container:
- build and push the new image to the registry locally
- depends on provider, e.g. AWS we can create new revision in task and update service

Downside:
- need to follow the rule from the cloud provider (not just use docker command anymore)