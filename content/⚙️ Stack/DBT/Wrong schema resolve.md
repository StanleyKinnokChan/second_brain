# Wrong schema resolve

- check the hierarchy of dbt_project.yml
- check the name is correct
- check the schema name was added if it is not the main part of the models (e.g. post-hook: ALTER TABLE **core.**dim_core__athletes ADD PRIMARY KEY (athlete_id))
- check there is no extra overide of custom schema