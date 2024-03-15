# Launch Configuration (LC) & Launch templates (LT)

- defined configuration of  EC2 in advance
    - AMI, instance type, storage & key pair
    - networking and security groups
    - userdata & AIM role
- both are not editable. Define one only and locked. LT has versions LC has not
- LT provide newer features - placement group, elastic graphic

Launch Configuration (LC)

- 1 use - as a part of autoscaling group
- not editable/ versioning

Launch templates (LT)

- as a part of autoscaling group/ launching EC2
- AWS adviced to use this
