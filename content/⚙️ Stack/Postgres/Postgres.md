---
title: 
tags:
---


**Set up using docker**
https://hub.docker.com/_/postgres

EXAMPLE: 
```
# Setup a most basic instance of postgres
docker run --name some-postgres -e POSTGRES_PASSWORD=mysecretpassword -d postgres:13-alpine

# Go into container bash, open psql to interact with postgres
docker exec -it some-postgres bash
psql -U <user_name>
```


**psql cheatsheet**
https://gist.github.com/StanleyKinnokChan/b1160d77647c56a184eb464ab92a332b

