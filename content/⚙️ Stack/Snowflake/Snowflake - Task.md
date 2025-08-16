---
title: 
tags:
  - Snowflake
---
A **task** in Snowflake is a database object that lets you run SQL statements (often `INSERT`, `COPY INTO`, or `CALL` to a stored procedure) **on a schedule** or **based on dependencies**.

- **Trigger**:
    - **Time-based** — uses CRON expressions or simple intervals using `SCHEDULE` syntax (e.g., every 5 minutes).
    - **Dependency-based** — runs only after another task completes using `AFTER` syntax, which generate a task graph
- **Common uses**:
    - Periodic `COPY INTO` from a stage to a table.
    - Data transformations in ELT pipelines.
    - Chaining tasks for multi-step workflows.


## Task creation workflow overview[¶](https://docs.snowflake.com/en/user-guide/tasks-intro#task-creation-workflow-overview "Link to this heading")

1. Create a [task administrator role](https://docs.snowflake.com/en/user-guide/tasks-intro#label-task-admin-role) that can run the commands in the following steps.
2. Define a new task using [CREATE TASK](https://docs.snowflake.com/en/sql-reference/sql/create-task).
    - [Assign compute resources](https://docs.snowflake.com/en/user-guide/tasks-intro#label-tasks-compute-resources)
    - [Define schedules or triggers](https://docs.snowflake.com/en/user-guide/tasks-intro#label-tasks-define-schedule-or-triggers)
    - [Define what happens when a task fails](https://docs.snowflake.com/en/user-guide/tasks-intro#label-tasks-failure-handling)
    - [Define additional session parameters](https://docs.snowflake.com/en/user-guide/tasks-intro#label-tasks-sessions-parameters)
3. Manually test tasks using [EXECUTE TASK](https://docs.snowflake.com/en/user-guide/tasks-intro#label-tasks-executing).
4. Allow the task to run continuously using [ALTER TASK … RESUME](https://docs.snowflake.com/en/sql-reference/sql/alter-task).
5. [Monitor task costs](https://docs.snowflake.com/en/user-guide/tasks-intro#label-task-monitoring-cost)
6. Refine the task as needed using [ALTER TASK](https://docs.snowflake.com/en/sql-reference/sql/alter-task).
Ref: https://docs.snowflake.com/en/user-guide/tasks-intro


### Compared with [[Snowflake - Dynamic table]]

| Feature / Aspect              | **Dynamic Table**                                    | **Dependency-based Task**                                |
| ----------------------------- | ---------------------------------------------------- | -------------------------------------------------------- |
| **Primary purpose**           | Keep a table automatically updated from a query      | Run SQL or stored procedures in a defined sequence       |
| **Trigger**                   | _Target lag_ interval (Snowflake manages refresh)    | Explicit `AFTER` dependency or schedule                  |
| **Execution control**         | Snowflake decides when to refresh to meet target lag | Full control over exact run order and timing             |
| **Workflow complexity**       | Single-step, SQL-only transformation                 | Multi-step workflows with branching and procedural logic |
| **Use with external systems** | Not supported                                        | Supported (e.g., send notifications, call APIs)          |
| **Non-SQL operations**        | Not possible                                         | Possible via stored procedures or external functions     |
| **Latency control**           | Approximate — Snowflake aims to meet target lag      | Exact — runs immediately after dependency finishes       |
| **Maintenance**               | Minimal — Snowflake handles refresh logic            | You manage scheduling, chaining, and enabling tasks      |
| **Best for**                  | Continuous, incremental data sync                    | ETL/ELT pipelines, staged loads, complex orchestration   |
