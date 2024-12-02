# test

test are assertions you make about your models and other resources in your dbt project, which ensures data quality through a testing framework. we should test 

1. during development - fixing bug before any production
2. deployment - continuously testing, rollback/ alert when failed
3. test in QA branch before code reaches main branch - reduce many versioning
4. opening pull requests (merging for CI purpose) - not allow PR to be merged if fail, aka CI testing (pre-commit is a framework that can be used to automatically run tests before committing files to git, leveraging git hooks.)

Testing should be **automated, fast, reliable, informative, and focused.**

**4 built-in Unit Test**
- unique
- not_null
- accepted_values: an list of values
- relationships (all of the records in a child table, the table being tested, should have a corresponding record in a parent table)

**Generic Test**
- a parameterized query that accepts arguments
- package/ build-in (e.g. not null)
- for customized one, write a {% test <test_name>(model, column_name) %} in the /test/generic folder
- add property in the model/ column in yml file
- run by dbt run/ dbt build…

>[!tip] Tips / Intuition
> When you write a test using where clause (e.g. ID>100), any row with a ID>100 returns error. In sort, a test that pass would have 0 row as a result of the test

```
Example of a not_null test is below. 

{% test not_null(model, column_name) %}  
  
select *  
from {{ model }}  
where {{ column_name }} is null  
  
{% endtest %}
```

**source freshness test**

- only work for raw data (source model in staging folder)
- use command dbt source freshness

**project test**

- test act on dbt_project.yml
- test the project as a whole
- good to use as a CI checks

**Behavior of failing the tests:**
dbt build: model0 → test → model1 →test…..Tests on upstream resources will block downstream resources from running, and a test failure will cause those downstream resources to skip entirely

**dbt build —fail-fast:** abort the whole operation immediately if there is any test failure

##### severity
- `severity`: `error` or `warn` (default: `error`)
	- error: check `error_if` first then check `warn_if`
	- warn: ignore error_if and check `warn_if`
- `error_if`: conditional expression (default: `!=0`)
- `warn_if`: conditional expression (default: `!=0`)
##### store-failture
when using —store-failture, a test result is stored in a default schema dbt_test__audit and it can be called by a SQL statement listed on the command line result. You can put the SQL into a new sql file and type dbt show -m <file_name> on command line to see the result.

##### store_failures_as
It is default as store-failture and you specify how the result should be stored. It can be:
- `ephemeral` — nothing stored in the database (default)
- `table` — test failures stored as a database table
- `view` — test failures stored as a database view
##### where
where config filter out the rows that need to be tested
