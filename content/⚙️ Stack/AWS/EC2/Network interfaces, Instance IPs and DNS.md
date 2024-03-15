# Network interfaces, Instance IPs and DNS

- Each instances has ≥1 Elastic network interface (ENI). ENI has to be same AZ as subnet and instance
- primary = secondary ENI, except secondary ENI can move and attach to other instances
- **Why want Secondary ENI**
    - generating MAC = allowing you to licensing
    - Multi-homed management & data
    - different security groups (separate each other)
- **Each network interface has**
    - a mac address
    - Primary IPv4 Private IP with DNS
    - 0≥ secondary IPs
    - 0/1 public IPv4 address with DNS (**changed if stopping and starting the instance**)
    - 1 elastic IP per private IPv4 address
        - associate with private IP on primary/second interface
        - old IPv4 will **lost forever** and replaced by the elastic IP
        - new IPv4 will be generated when elastic IP is removed
    - 0≥ more IPv6 address
    - security group
    - source/ destination check (must disable source/destination checks if the instance runs services such as NAT, routing, or firewalls)

**Noted that**

- no visibility public IPv4 inside OS
- IPv4 public IPs are dynamic: change if stop & start, assign elastic IP to avoid this
- Direct communication between instances and world outside
    - Inside VPC public DNS resolves to private IP
    - Outside VPC public DNS resolves to pubic IP
