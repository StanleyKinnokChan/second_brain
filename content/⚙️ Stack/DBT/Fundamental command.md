# Fundamental command

| dbt compile | generates executable SQL from source model, test, and analysis files. Convert the jinjer reference to the resource name |
| --- | --- |
| dbt run | executes compiled sql model files against the current target database |
| dbt source freshness |  |
| dbt test | dbt will tell you if each singular or generic test in your project passes or fails |
| dbt docs generate | generating your project's documentation website |
| dbt build | All-in-one:
- run models
- test tests
- snapshot snapshots
- seed seeds |
| dbt run-operation {macro} --args '{args}’ | invoke a macro |