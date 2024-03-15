# small knowledge & trick

- you have to move inside the project folder to run a successful dbt command
- source name can be different from database/ schema name
- name of table in source.yml is case sensitive for Jinja reference, but need not follow the case in the database (although good to follows)
- check the plural of properties of yaml if error
- **dbt run --select staging.*** can run all the models in a subdirectory “staging”
- file name can affect the reference
- Tags cannot be directly applied in the model schema.yml. They should be added to dbt_project.yml
- no ; is needed after SQL statement
- capitalization matter when creating model/ call dbt command