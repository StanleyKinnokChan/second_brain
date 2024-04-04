---
title: 
tags:
---
#### **Why docker important?**
- Reproducibility
- CI/CD
- Environment isolation
- Dependent speciftion
- Integration tests
- running pipeline in cloud
- local experiments

#### **Terminology:**
**Docker:** a way to package software so it can run on any hardware. Developers can download the images and run the applications with exact env. Configuration provided
**Dockerfile:** Blueprint for image
**Image:** template for running container, which is an Immutable snapshot
**Container:** a running process


**Setup a most basic instance** (just run the f):
```
docker run --name some-postgres -e POSTGRES_PASSWORD=mysecretpassword -d postgres:13-alpine
```



**Reference:** 
[[Quick Docker cheatsheet]]
[[Dockerfile]]