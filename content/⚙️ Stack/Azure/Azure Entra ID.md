---
title: 
tags:
  - Azure
  - Security
---
- to be known as Azure Active Directory (run on cloud and use protocals like SANK and Oauth), but not replacement of active Directory (run on server and use protocals like LDAP  & kerberos).
- Identity management 
- use APIs to connect the app for authentication & authorization
- In Entra model, app exchange credential and token with identity provider, then the app takes the signed token to the server the identity provide gave truest key to

Benefit
- Security
- Threat control (e.g. look at login pattern)
- Reduce development time for app
- centralize administration
- Single sign-on
- Integrates with other Azure services

Azure AD conditional access:
- requires extra step for those uncommon login (suspicious time/ location/haven't login for a long time/ device never used before)

Azure global administrator can config user [[MFA]] for free

Three basic roles 
- Owner (full access & assign permission)
- Contribution (full access only)
- Reader (only read, no change of setting)