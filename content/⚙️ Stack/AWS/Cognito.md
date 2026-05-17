---
title: Cognito
tags:
  - aws
---

# Cognito

- **authentication**, **authorization** & **user management** for web/mobile apps
- user directory management & profiles, sign-up & sign-in, MFA

<aside>
💡 **User pools** are for [authentication](https://docs.aws.amazon.com/cognito/latest/developerguide/authentication.html) (identity verification). With a user pool, your app users can sign in through the user pool or federate through a third-party identity provider (IdP).

**Identity pools** are for authorization (access control). You can use identity pools to create unique identities for users and give them access to other AWS services.

</aside>

- **user pools -** sign-in & get a json web token (JWT)
    - most services cannot be accessed by JWT but AWS credentials via identity pool
- I**dentity pools** - accept the user pool token & allow you to use temporary AWS credentials, by assuming IAM role, to access AWS resources
    - **unauthenticated identities** - guest users
    - **Federated identities** - SWAP - google, FB, twitter…

    [[Cognito/Untitled.png]]
