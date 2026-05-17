---
title: Docker compose
tags:
  - docker
---
- great for managing multiple containers on the same host for an integrated application
- does not replace dockerfiles for custom images



### YML configuration

Example structure
```
name: myapp

services:
  foo:
    image: busybox
    command: echo "I'm running ${COMPOSE_PROJECT_NAME}"
```

To use a custom image that haven't build yet, use build element
```

services:
  foo:
    build:
	    content: <folder/that/hold/dockerfile>  
	    dockerfile: Dockerfile   #name of the dockerfile
		arg: # we can also supply the runtime arg for the build
			some_arg: some_value 
```

```

port publishing (aka forwarding/mapping)
```
services:
	foo:
		ports:
			- '80:80'
```

service dependency:
```
services:
	foo:
	boo:
		depends_on: foo
```

### common command

```
# -d = in detached mode (run on the background without terminal)
docker-compose up -d
```

```
# stop all container, -v also remove the volume we defined
docker-compose down -v
```

```
# build the missing image in the custom build, without starting a container
docker compose build
```

```
# rebuild docker compose
docker compose up -d --no-deps --build <service_name>
```


## Naming
- by default, the container name would be folderName-ServiceName
- you can override it
```
servies:
	foo:
		container_name: <my_service_name>
```