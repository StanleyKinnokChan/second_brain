# deployment

deployment 

**TYPE:**

**Standard job -** this jobs is typically just **dbt build** and will rebuild your entire DAG while **including** incremental logic.

**Full refresh job -** this job similar will use **dbt build** except it will pass the full refresh flag. This will force incremental models to be dropped and materialized from scratch and seeds to be dropped and rebuilt as well.

**Time sensitive** - this is a job that usually has a time sensitive business use case. You might consider refreshing marketing data or sales data more frequently than your standard job. You can accomplish this by using model selector syntax with your commands.

**Fresh rebuild** - fresh rebuild allows you to **only** rebuild models downstream from sources that have been updated since the previous run.

Simple orchestration: 2 job no overlapping time

![Untitled](deployment%20af985f9430c9460188856d4faa7d8653/Untitled.png)

More complex orchestration: 2 job with overlapping time updating same models, which has to avoid.

time slot has to be spared for the full-refresh to happen, so we need to create 3 jobs

1. regular run from Mon to Sat
2. Sunday regular run without a period of time
3. Sunday full refresh run 

![Untitled](deployment%20af985f9430c9460188856d4faa7d8653/Untitled%201.png)

CI 

![Untitled](deployment%20af985f9430c9460188856d4faa7d8653/Untitled%202.png)

SlimCI: **Slim CI** refers to smart way of running a CI build by only building and testing models that have been updated and those downstream of them.

- add —state:modified+ to only run the model that have been modified, the state flag will compare to the manifest file from the previous run to select the models.

In cloud

create a job (run on pull request) → commit modified code to git → job triggered by the pull request