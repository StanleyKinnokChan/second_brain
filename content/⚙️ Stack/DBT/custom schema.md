# custom schema

- the priority of schema usage:
    - config block in the model > property in dbt_project > schema name
- two way to control
    - add {{ config(schema=’<schema_name>’) }}
    - specify a property in dbt_project.yml

- override the macro