# Instance Roles & Profile

- permission policy allows permission that the policy would grant
- IAM role with permission policy allows EC2 service to assume it, providing temporary credential
- instance profile containing IAM roles attach to the instance
- temp credentials delivered via instance meta-data, which was accessed by application to access the permitted resources. The temp credential rotated automatically (no expires)
    - iam/security-credentials/role-name
- role always better then adding long-term access keys into instance
- CLI tools will use role credentials automatically

[[Instance Roles & Profile/Untitled.png]]
