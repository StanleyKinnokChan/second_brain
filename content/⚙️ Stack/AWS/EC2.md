# EC2

[[Virtualization]]

- **Overall:**
    - EC2 are virtual machines (OS+resources)
    - **Amazon machine image** refers initial software configuration of an instance
    - EC2 instances run on EC2 shares/ dedicated host
    - AZ resilient, hosts = 1 AZ
    - instances+EBS /volume can only be contained in the same AZ, cannot be transferred across AZ
    - if an instance stop and start again (not restarting), the host will be different but within the same AZ
    - Although a public IP address is associated with the EC2 server, the public address is not configured on the server itself. Instead, your VPC's Internet Gateway has the public address and it performs address translation.
    - Use case
        - traditional OS+application compute
        - long-running compute (for years)
        - server style application
        - need burst/ steady-state load
        - monolithic application stacks
        - migrated application workloads/ disaster recovery

[[Connection]]

[[Scaling]]

[[EC2 Instance Type]]

[[EBS and instance Storage]]

[[Network interfaces, Instance IPs and DNS]]

[Amazon Machine Image (AMI)](EC2%2084bcb0e5274547d7bca455264ed619be/Amazon%20Machine%20Image%20(AMI)%20bfd0a61695104914ab161f45468d3723.md)

[[EC2 Purchase Options ]]

[[Instance status checks, Auto-recovers & Termination]]

[[Instance Metadata]]

[[EC2 instance store]]

[[Bootstrapping using User Data]]

[[Instance Roles & Profile]]

[[SSM parameter Store]]

[[System and application logging]]

[[Placement Groups]]

[[Enhanced networking & EBS Optimized]]
