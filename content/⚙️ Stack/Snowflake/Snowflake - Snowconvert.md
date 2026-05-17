---
title: Snowflake - Snowconvert
tags:
  - snowflake
---
Snowconvert is a source **code conversion tool** with [[Snowflake]] as the only target platform. It is not a Migration Suite. SnowConvert is explicitly built for code conversion only and does not perform many other functions needed to complete a full migration. SnowConvert only **converts** code. It does not migrate data or facilitate testing, optimization and data validation.

| **SnowConvert DOES:**                                                                                                                                              | **SnowConvert does NOT:**                                                                                                                                                                                                                     |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| - Perform code conversion<br>    <br>- Provide reports detailing conversion rates & insights on code complexities<br>    <br>- Output functionally equivalent code | - Perform all migration activities<br>    <br>- Migrate data<br>    <br>- Facilitate testing & data validation<br>    <br>- Connect to any systems<br>    <br>- Deploy converted code<br>    <br>- Optimize code for performance on [[Snowflake]] |


**SnowConvert** generates a **model** of the source language alongside a **symbol table,** enabling the reconstruction of code into [[Snowflake]]. 

assessment functionality:
- potential complexities of the source code
- detailed reporting on what it has converted
- what code may need additional review to confirm a correct conversion
- what it cannot convert.

**Supported Source Platforms**
- Teradata 
- Oracle
- SQL Server

---
#### **The Iterative process**

SnowConvert receives automatic updates for translations and other functionality typically on a two-week basis. As such, rather than running all code through the tool at once initially, it is best to use SnowConvert against portions of the code iteratively throughout the migration.

This may help improve your project's overall conversion rate over time, by reporting code scenarios that may not yet be automated but are essential to your migration. It also allows you to test converted code incrementally to identify early on if the code performs to expectation in [[Snowflake]] or if refactoring of the code may become necessary.


4 steps
1. Review and prepare input code
   build your conversion plan, dividing up code into portions that make sense based on your overall migration plan. Then extract, review, and prepare the input code. Be sure to identify and remove code that you do not want to convert, such as back-ups, system-specific code like statistics gathering, or DBA task-based code that will not be relevant in Snowflake.
2. Running the Conversion. 
   run the tool to access the Assessment reports. SnowConvert will provide you with reports to help you understand the quality of the input code and what changes you should make to accelerate the conversion. It will also let you know if the code submitted has missing dependencies. This is critical, as the best conversion rates depend on understanding all dependencies.
3. Rerunning the Conversion
   First, you evaluate the reports and output code, and then you modify your input code to execute conversions. Finally, you rerun SnowConvert.
4. Manual Refactoring
	Based on your output results, make additional manual code adjustments and merge those changes with the converted code to be implemented, tested, and deployed.

Questions to ask:
- Why? what is the goal? What is the priority and their dependencies?
- Role? Who is involved? Theier responsibility and activities they engaged in?
- Time & effort? How much time and resources needed?

----
#### **SnowConvert component**

1. Migration planning
2. Database Conversion
3. Data Migration
4. Data Integration
5. Data Validation
6. Data Consumption
7. Infrastructure & Environments (SSO/ security, architecture)
8. Performance & Cost Optimization (workload management/ tuning)
9. Project management (timeline, sprints/ duration and categories of work)
![[snowconvert_component.png]]


----
##### **Object Inventory for SnowConvert**

Creating an object inventory for each phase of the migration and each migration category is vital. Object inventories should include a list and count of all object types per environment, such as production, UAT, development, etc. 

Identify and document the activities needed to complete the migration for each type of object and provide an effort estimate for all activities identified. Example activities may include setup, design, code modification, all testing, asset management, and status reporting.


---
##### Two Phases: Assessment and Conversion

Assessment phase
SnowConvert will scan the code and provide a high-level inventory of all the different code units found. It will also provide a report of the conversion issues found in the code, allowing the migration team to understand the complexity of the code conversion project. This report is valuable during the project's planning phase, providing input to design the timeline.

**Conversion**
pre-process
DDL Extraction & inventory assement, it can be done by the provided scripts

**Running the conversion**
- config the conversion settings
- get the access codes

Viewing Conversion result
- Code Completeness Score (e.g. indicating missing objects)
- Excluded scope (the file format/ language that is not supported)
- Code Units Summary (the stat of different code unit)
- Conversion Remarks Details (the difference in functionality, required review)
- Errors, warnings & issues
- different Detailss breakdown...