# YAML

YAML is the configuration file for each component of our model, it contains:

1. **Project Configuration:** It contains project-wide configurations, such as the target data warehouse connection, profile information, and other project-level settings. This allows you to define your project's connection details, data sources, and other global settings in one place.
2. **Dependency Management:** dbt allows you to define dependencies between models and sources in your project. These dependencies are typically defined in the **`dbt_project.yml`** file. This means you can specify which models should be run before others, ensuring that your transformations are executed in the correct order.
3. **Materialization and Customization:** You can specify how dbt should materialize (create and manage) the tables and views in your data warehouse. Different data warehouses have different capabilities, and you can customize how dbt generates SQL code for your specific data warehouse in the **`dbt_project.yml`** file.
4. **Documentation and Metadata:** You can add descriptions and metadata to your models, columns, and other objects in your project using the **`dbt_project.yml`** file. This makes it easier for your team members to understand and work with your data models.
5. **Environment Configuration:** The **`dbt_project.yml`** file allows you to define different environments (e.g., development, staging, production) and set environment-specific configuration options. This is essential for managing different deployment scenarios and ensuring consistency across environments
- 

SQL file write the relationship and transformation logic, referecing the table using CTE