---
title: 
tags:
---
A Dockerfile is **a text document that contains all the commands a user could call on the command line to assemble an image**. This page describes the commands you can use in a Dockerfile.

Example of an dockerfile
```
FROM python:3.9-alpine
RUN pip install pandas
WORKDIR /app
COPY pipeline.py pipeline.py
ENTRYPOINT [ "python", "pipeline.py"]
```



reference: https://docs.docker.com/reference/dockerfile/#:~:text=A%20Dockerfile%20is%20a%20text,can%20use%20in%20a%20Dockerfile.