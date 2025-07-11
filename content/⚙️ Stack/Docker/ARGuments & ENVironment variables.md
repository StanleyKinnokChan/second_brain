---
title: 
tags:
---
ARG:
- available inside of Dockerfile, Not accessible in CMD or any application code
- set on image build via --build-arg

ENV:
- available inside of dockerfile & in application code
- set via ENV in dockerfile, or via --env on docker run
- or add .env file and use a --env-file <.env file> option on docker run