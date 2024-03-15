# Identity Access Management (IAM)

- Manages long-term access of AWS users and resources (use ARN)
    - Type

        [[Identity Access Management (IAM]]%2067545689bf024a28b9cce33e9b6b6002/Untitled.png)

- **5,000** IAM users per account (use IAM role/ federation if exceeds)
- an IAM user can be a member of 10 groups
- IAM groups (like a label)
    - are containers for users
    - not a true identity ⇒ can’t be referenced as a principal
    - have no credential
    - no limit of group members
    - no nesting
    - limit 300 group per account

[IAM roles](Identity%20Access%20Management%20(IAM)%2067545689bf024a28b9cce33e9b6b6002/IAM%20roles%205f61935173d04773b8d12dca75663c1d.md)

**Principle:** a thing (user, device, application, process) whose access is managed

**Authentication:** Principle request access by providing U&P or Access keys to IAM

**Authorization:** AWS checked with IAM to allow/ deny principle use the service

**Policy**

- (≥1) security statement to grant acacess
- types of policies

    [[Identity Access Management (IAM]]%2067545689bf024a28b9cce33e9b6b6002/Untitled%201.png)

- policy structure

    [[Identity Access Management (IAM]]%2067545689bf024a28b9cce33e9b6b6002/Untitled%202.png)

- Priority applies when there are contradiction
    1. explicit deny
    2. explicit allow
    3. Default (implicit) deny

- password policies

    [[Identity Access Management (IAM]]%2067545689bf024a28b9cce33e9b6b6002/Untitled%203.png)

- Programmatic Access Key

    [[Identity Access Management (IAM]]%2067545689bf024a28b9cce33e9b6b6002/Untitled%204.png)

- multi-factor authentication (MFA)
    - admin can only allow the option, using it or not depends on the users’ choice
    - but admin the restricts access to certain resources

    [[Identity Access Management (IAM]]%2067545689bf024a28b9cce33e9b6b6002/Untitled%205.png)


- How can policy work in different ways
    - role can be assigned to a user, group, or even resources themselves
    - single role can have multiple policies

        [[Identity Access Management (IAM]]%2067545689bf024a28b9cce33e9b6b6002/Untitled%206.png)

    - policies can attach the role, or user (inline policies)

[AWS organization](Identity%20Access%20Management%20(IAM)%2067545689bf024a28b9cce33e9b6b6002/AWS%20organization%20b31b965c23824083a89bd3e1304dc394.md)
