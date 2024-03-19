---
title: 
tags:
---
![airflow tasklifecycle](https://miro.medium.com/v2/resize:fit:1400/1*InPlDqSLBeGiLVWSZJyCWQ.png)

When a DAG run is triggered, tasks are going to be executed one after another according to their dependencies, Each task will go through different stages from start to completion. Every stage indicates a specific status of the task instance. There are 11 status in total.

| status            | meaning                                                                                                        |
| ----------------- | -------------------------------------------------------------------------------------------------------------- |
| no_status         | scheduler created empty task instance                                                                          |
| scheduled         | scheduler determined task instance needs to run                                                                |
| queued            | after scheduling, scheduler sent task to executor to run on the queue and execute the task once worker is free |
| running           | worker has picked up the task and running it                                                                   |
| success           | task is success                                                                                                |
| removed           | task is removed                                                                                                |
| upstream_failed   | the task's upstream task failed                                                                                |
| up_for_reschedule | running task is waiting to be reschedule due to specific cases                                                 |
| skipped           | task is skipped                                                                                                |
| failed            | task is failed                                                                                                 |
| shutdown          | task is aborted                                                                                                |
| up_for_retry      | when task is failed or shutdown, it will rerun if the maximum retry number is not yet reached                  |
