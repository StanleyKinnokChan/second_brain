---
title: 
tags:
---

##### Catchup
By using catchup inside a DAG, you can run the DAGs in the the historical period at the designated interval up to the lastest interval if the DAG was not ran before. If all DAG was run before at all interval (aka no need to catch-up), the DAG will only be ran at the latest interval. 

##### Backfill
Going to bash of container and run backfill in CLI, the DAG will be run/ re-run within the date range at the designated interval no matter if the DAG was run before. The run type of the running result will be marked as "backfill".

Example:
```
docker ps
docker exec -it 9dbdc1e42a0c bash
airflow dags backfill -s 2024-02-27 -e 2024-03-04 dag_with_catchup_backfill_v01
```
