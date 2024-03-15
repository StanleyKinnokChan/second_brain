# IAM roles

- can be both internal/ external
- = level of access in a short period of time with a temporary security credentials
- 2 policy can be attached
    - trust policy
    - permissions policy
- Use case
    - AWS lambda without the need of hard code access key
    - don’t know the number of users/ principle
    - emergency/ out of usual
    - external accounts that are not able to use AWS directly
    - >5000 users that you cannot add all of them as IAM users
    - Federation trust other web identities and allow them to access AWS resources via IAM role (particularly in mobile application)

**Service-linked roles**

- IAM role linked to a specific AWS service, people can use this role to modify the service via this role after gaining a PassRole permission
- predefined by AWS service include all the permissions that the service requires to call other AWS services on your behalf
- cannot delete the role until it isn’t needed anymore (Before you can delete the roles, you must first delete their related resources)
- create by the service itself/ allow you to create it
