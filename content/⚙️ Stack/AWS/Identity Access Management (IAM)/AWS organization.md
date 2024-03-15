# AWS organization

- allow business to manage multiple AWS accounts in a cost-effective way with little management overhead
- multiple account = separate user pool and bills
- use a master ./ management account to create a organization, then
    - invites other accounts into the organization (member account), or
    - create new account with the organization
- account can be grouped (organizational units) and form hierarchy starting from an organization root
- consolidate billing → all go to master account, the total spending is reserved → discount
- don’t need IAM user every single AWS acc, IAM role can be used for IAM user to access other account
- **role switch** → use identity federation/ IAM identity and switch to other account (via a IAM role)
    - if the account is created within the org., the role has been added
    - if the account is invited one, the role has to be added from IAM
- contain **service control policies (SCP)**
    - **= acc permission boundaries** → restrict what the account can do (included acc root user)ds
    - **don’t grant any permissions, just limit possible permission can be granted**
    - can be attached to the org, org unit/ individual acc
    - management account cannot be restricted by SCPs
    - FullAWSAccess as default, by removing this, everything is implicitly denied.
    - we can also explicitly deny specific resources
