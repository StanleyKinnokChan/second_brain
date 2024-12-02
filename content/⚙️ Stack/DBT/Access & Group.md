---
title: 
tags:
  - dbt
---
The access config can adjust if a model can be accessed at different level

| Access    | Referenceable by                                                                          |
| --------- | ----------------------------------------------------------------------------------------- |
| private   | Same group                                                                                |
| protected | Same project/package                                                                      |
| public    | Any group, package, or project. When defined, rerun a production job to apply the change. |
The group config is a customized tag to categorize the model. 

e.g. A model in "Finance" group with private access can only be accessed by other model in "Finance" group but not by those in other groups such as "HR". 