# SSM parameter Store

- SSM = system management
- storage for **configuration** & **secrets** 
	- Security through IAM
	- Version tracking
	- Hierarchies allowed (e.g. name = /my-department/my-app/dev/db-password)
		- then --path flag can be used in CLI to retrieve all parameters under this paths
	- Plaintext, or Ciphertext via KMS (optional)
- 3 types:
	- String
	- StringList: list of string seperated by comma
	- SecureString: encrypted by KMS
- Notifications with Amazon EventBridge
- Integration with CloudFormation
- license codes, database strings, full configs & passwords
- public parameters - latest AMIs per region

**Parameters Policies** (for advanced tier)
- Allow to assign a TTL to a parameter (expiration date) to force updating or deleting sensitive data such as passwords
- Can assign multiple policies at a time
- Notification via EventBridge

