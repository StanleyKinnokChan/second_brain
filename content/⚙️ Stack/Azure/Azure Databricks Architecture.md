---
title: Azure Databricks Architecture
tags:
  - azure
---
![[Azure Databricks Architecture.png]]
 - Seperate into 2 parts: control & data plane
 - When creating Databrick resource, 4 resources are being created in the backend as data plane (incl. VNet, security groups, the storage, databricks workplace)
 - When logging in databricks using Azure AD, databricks access the data plane and interact with the data plane to retrieve the resource created (i.e. users have full control on the data plane side where databricks platform maintain the backend such as cluster manager and DBFS). 