---
title: 
tags:
---
![[Pasted image 20240314165259.png]]

### **TLDR**


Find the name or ID of the image
```
docker image ls
```

Find the name or ID of the container
```
docker ps
```

Build container from the dockerfiles (customerize)
```
Docker build [-t <container_name>] <folder location (eg .)>
```

Use the docker run command to initiate the container using the image. Automatically pull image if not exist locally
```
docker run --name some-postgres -e POSTGRES_PASSWORD=mysecretpassword -d -p 5432:5432 postgres:13-alpine
```
or  use -it to open interactive mode to use the bash within containers
```
Docker run -it < image name> bash   
```

Use the docker exec command to start a shell inside the container. Replace **“container_name_or_id”** with the name or ID of the container.
```
docker exec -it <container_name_or_id> bash
```

