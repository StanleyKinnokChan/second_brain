---
title: Airflow asset
tags:
  - airflow
---
Asset is a way to build the dependency between the DAGs in a event-driven way. 
After the dags do somethings, you can send the event to the assets, every dag that is a consumer of the asset will be triggered. 

@Asset itself is a dag to create asset (asset producer)