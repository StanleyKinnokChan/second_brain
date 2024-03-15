# Introduction of Containers

**Vitualisation Problems**

- guest OS comsume all the resource, where they are pretty much the same

[[Introduction of Containers/Untitled.png]]

**Containerization**

- each container contains less memory
- container only runs the application & environment it needs
- no full OS needed, and able to run much more application in isolation
- portable and lightweight - filesystem layer are shared

[[Introduction of Containers/Untitled 1.png]]

**Docker image = container copy**

- dockerfiles are used to build images
- images are create from a base image or scatch (barely minimal for a OS)
- layers on the base to generate a differential architecture

[[Introduction of Containers/Untitled 2.png]]

- docker image create docker container, which has additional read-write file system layer
    - different read-write file system layer → made different containers
    - Container Registry (public = docker hub)
