---
title: Airflow @set @teardown
tags:
  - airflow
---
The main use of the set and teardown to ensure the resource lifecycle is managed. the task is placed between set and teardown. So if the task is re-run or stop, it is ensured that the corresponding resource also get created/ destroyed. 

```
@setup 
def outer_setup()
	return "some cluster id"
	
@tear down
def outer_teardown(cluster_id):
	...
	
@task
def outer_work()
	...
	
s = outer_set()
w = outer_work()
t = outer_teardown()

s >> w >> t

```