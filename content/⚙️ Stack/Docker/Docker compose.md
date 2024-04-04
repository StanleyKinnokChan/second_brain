---
title: 
tags:
---

```
# -d = in detached mode (run on the background without terminal)
docker-compose up -d
```



```
# -v also remove the volume we defined
docker-compose down -v
```

```
# rebuild docker compose
docker compose up -d --no-deps --build <service_name>
```