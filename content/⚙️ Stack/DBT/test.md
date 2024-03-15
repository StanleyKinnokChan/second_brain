# test

test are assertions you make about your models and other resources in your dbt project, which ensures data quality through a testing framework. we should test 

1. during development - fixing bug before any production
2. deployment - continuously testing, rollback/ alert when failed
3. test in QA branch before code reaches main branch - reduce many versioning
4. opening pull requests (merging for CI purpose) - not allow PR to be merged if fail, aka CI testing (pre-commit is a framework that can be used to automatically run tests before committing files to git, leveraging git hooks.)

Testing should be **automated, fast, reliable, informative, and focused.**

when you write a test using where clause (e.g. ID>100), you are testing there would be row that return error (error if ID>100) 

generic test

- a parameterized query that accepts arguments
- package/ build-in (e.g. not null)
- for customized one, write a {% test <test_name>(model, column_name) %} in the /test/generic folder

![Untitled](test%207dda7036a441469aa2a758ea589d4f0f/Untitled.png)

- add property in the model/ column in yml file
- run by dbt run/ dbt build…

specific test

- defined in a separated test folder
- customized and reusable

source freshness test

- only work for raw data (source model in staging folder)
- use command dbt source freshness

project test

- test act on dbt_project.yml
- test the project as a whole
- good to use as a CI checks

Reason of test:

![Untitled](test%207dda7036a441469aa2a758ea589d4f0f/Untitled%201.png)

[what to test](test%207dda7036a441469aa2a758ea589d4f0f/what%20to%20test%20d80b0c84bce4483e91433315f9095378.md)

![Untitled](test%207dda7036a441469aa2a758ea589d4f0f/Untitled%202.png)

![Untitled](test%207dda7036a441469aa2a758ea589d4f0f/Untitled%203.png)

dbt build: model0 → test → model1 →test…..Tests on upstream resources will block downstream resources from running, and a test failure will cause those downstream resources to skip entirely

dbt build —fail-fast: abort the whole operation immediately if there is any test failure

**—store-failture**

when using —store-failture, a test result is stored and it can be called by a SQL statement listed on the command line result. You can put the SQL into a new sql file and type dbt show -m <file_name> on command line to see the result.

![Untitled](test%207dda7036a441469aa2a758ea589d4f0f/Untitled%204.png)

[package](test%207dda7036a441469aa2a758ea589d4f0f/package%207e1c1316e1004281862fe8a708aa5a60.md)

[test Configuration](test%207dda7036a441469aa2a758ea589d4f0f/test%20Configuration%20a90733120afa4499bf774292b0f91760.md)

[Deployment](test%207dda7036a441469aa2a758ea589d4f0f/Deployment%20a748dc0dae7b4c6a88e64d46950597b5.md)