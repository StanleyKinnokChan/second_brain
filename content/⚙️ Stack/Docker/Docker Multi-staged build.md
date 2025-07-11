---
title: 
tags:
---
Analogy:
You bake bread → You deliver just the bread,  
not the oven, flour bags, or dirty bowls.

Same thing:  
Final container = just runtime + final files,  
not the whole build environment.

```
FROM alpine:latest AS base    # assigned a name in a FROM => a stage
RUN apk --no-cache add build-base

FROM base AS build1     # build upon the previous stage
COPY source1.cpp source.cpp
RUN g++ -o /binary source.cpp

FROM base AS build2
COPY source2.cpp source.cpp
RUN g++ -o /binary source.cpp
```

You can either build the complete image or select individual stages
```
# target name can specify the stages needs to be build
docker build --target base -f <dockerfile_path>
```

https://docs.docker.com/build/building/multi-stage/
