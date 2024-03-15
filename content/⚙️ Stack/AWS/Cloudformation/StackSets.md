# StackSets

<aside>
💡 A ***stack set*** lets you create stacks in AWS accounts across regions by using a single CloudFormation template. It extends the capability of stacks by enabling you to create, update, or delete stacks across multiple accounts and AWS Regions with a single operation.

</aside>

<aside>
💡 A **stack instance** is a reference to an attempted or actual stack in a given account within a given Region. A stack instance can exist without a stack—for example, if the stack couldn't be created for some reason. A stack instance is associated with only one stack set.

</aside>

- deploy CFN stacks across **many accounts & regions**
- **StackSets** are **containers** in an **admin account**
    - contain multiple stack instances, which references the actual stacks running in specific regions & accounts
    - **stack instances** & **stacks** are created within ‘**target accounts**’
    - each stack = 1 region in 1 acc
    - security = **self-managed** or **service-managed via IAM roles**

[[StackSets/Untitled.png]]

**Term:**

- concurrent accounts: how many accounts involved for stack creation
- Failure tolerance:
- **Retain stacks:** the stacks that are retained after removing stack instances from stack sets
