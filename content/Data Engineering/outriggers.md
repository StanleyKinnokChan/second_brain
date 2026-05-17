---
title: outriggers
tags:
  - data-engineering
  - data-modelling
---
A table or entity that is included in a hierarchy but is not directly related to the fact table are known as outriggers. Outriggers are often used when a dimension table or entity is referenced by another dimension. The primary key of an outrigger is referenced by the foreign key of a dimension table or entity.

For instance, a bank account dimension can reference a separate dimension representing the date the account was opened. Outrigger dimensions are permissible, but should be used sparingly. In most cases, the correlations between dimensions should be demoted to a fact table, where both dimensions are represented as separate foreign keys.

