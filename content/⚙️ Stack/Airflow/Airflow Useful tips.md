---
title: 
tags:
---
To test a task, go inside the container and run this:
```
docker exec -it <container_name> /bin/bash
airflow tasks test <DAG name> <task name> <a date like 2022-01-01>

```