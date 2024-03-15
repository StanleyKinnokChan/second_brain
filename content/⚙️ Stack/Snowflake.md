# Snowflake

- what is the cloud
    - agility: flexibility, innovate fast
    - elasticity (don’t have to over-provision resources upfront, use and increase when needed)
    - cost savings (trade capital expenses for variable expenses, only pay for what you use. Economy of scale)
    - deploy globally: expand to new geographic areas and deploy in minutes
- type of cloud computing
    1. Infrastructure as a Service (IaaS): This type of cloud service provides virtualized computing resources over the internet, such as virtual machines, storage, and network resources. Customers can rent these resources on-demand and use them to host their own applications and data. Examples of IaaS providers include Amazon Web Services (AWS), Microsoft Azure, and Google Cloud Platform.
    2. Platform as a Service (PaaS): PaaS is a cloud computing service that provides customers with a platform to develop, run, and manage their applications and services. It includes operating systems, databases, middleware, and other necessary tools for developing and deploying applications. Examples of PaaS providers include Heroku, Google App Engine, and AWS Elastic Beanstalk.
    3. Software as a Service (SaaS): SaaS is a cloud computing service that delivers software applications over the internet, typically on a subscription basis. Customers do not have to worry about installing, maintaining, or upgrading the software, as the provider takes care of these tasks. Examples of SaaS providers include Microsoft Office 365, Salesforce, and Google Workspace.
- why region selection matters:
    - latency: Reduce data latency if being closed to the targeted user base to
    - cost: saving cost (due to land, electricity, bandwidth)
    - legal compliance: compliance and regulatory requirements for data to reside within the region itself
    - features: not all regions provide all AWS feature
- Availability zone
    - each region consists of multiple isolated locations
    - each is physically independent

- Snowflake features
    - “data warehouse as a service”
    - Database products in the cloud
    - Competitors: (Databricks, google big query, amazon redshift)
    - special features
        - fully managed on the cloud of your choosing
        - no back-end maintenance
        - fully serverless model (scales)
        - no limits on storage capacity
        - price per second of computing
        - data sharing between accounts/ clients
    - price :use credit model: mostly measured by computing power
    - great area of the snowflake
        - ALL SQL interface
        - document storage
        - JSON dot notation query & flatten
        - linear vs stair step scaling

        [[Snowflake/Untitled.png]]

    - the term “**snowflake warehouse”**
        - =/= data warehouse
        - name of the processing power for executing queries in snowflake
        - bigger warehouse = more compute power = faster queries
- The tabs in the snowflake database
    1. **Stages:** A stage in Snowflake is a named location where data files are stored temporarily before being loaded into a table. Stages can be either internal, meaning that they are stored within Snowflake, or external, meaning that they are stored outside of Snowflake in cloud storage services such as Amazon S3 or Microsoft Azure.
    2. **File Formats:** Snowflake supports a variety of file formats including CSV, JSON, Avro, ORC, Parquet, and others. File formats can be specified when data is loaded into a table and can impact the performance and efficiency of the load process.
    3. **Sequences:** A sequence in Snowflake is a database object that generates unique numeric values. Sequences are often used as the primary key for a table to ensure that each row has a unique identifier.
    4. **Pipes:** A pipe in Snowflake is a mechanism for loading data into a table in a stream-oriented manner. Pipes allow data to be loaded in real-time from a data source into Snowflake, allowing for near real-time data analysis and reporting.

normalize database - 3nf

command

- list @<name of the stage>

    see all the file within the stage


account usage:

- query_history:
- query tagging

[[Architecture]]

[[Data masking]]
