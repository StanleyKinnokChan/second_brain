# Amazon Machine Image (AMI)

- can be used to launch EC2 instance
- AWS/ community provided/ marketplace (include commercial software)
- AMI are regional with unique ID
- can create an AMI from an EC2 instance that have been configured

**AMI lifecycle**

[[Amazon Machine Image (AMI]]%20bfd0a61695104914ab161f45468d3723/Untitled.png)

- AMI itself doesn’t contain any real data volume, it refers the snapshot generated from the previous volume

**KeyPoint**

- AMI= region specific, but can be copied between regions
- AMI baking = creating an AMI from a configured instance + application
- AMI cannot be edited (have to create a instant and bake another AMI)
- permissions (access to AMI) default to be only your account, but also can be set as public/ specific account
- bill applied for instance with EBS because snapshot is created
- snapshot will be copied to new region when AMI is copied to new region
