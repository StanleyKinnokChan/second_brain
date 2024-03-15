# VPC

- **Overalls**
    - isolated network regional service across AZs
    - nothing in or out without explicit configuration
    - flexible configuration - simple or multi-tier
    - hybrid networking
    - **5 VPC per region**
    - **DNS**

        Fully featured DNS provided by route 53

        DNS = VPC ‘Base IP +2’ address

        critically setting to DNS

        - *“enableDnsHostnames”*- gives instances DNS Names
        - *“enableDnsSupport“* - enables DNS resolution in VPC
    - **IP**
        - Default cidr: 172.31.0.0/16
        - VPC min. /28 (16IP) to max. /16 (65536IPS)
        - default 0.0.0.0/0 = all possible IP addresses =  allowing all public traffic from the internet
    - Default or dedicated tenancy (very expensive, spare the whole resource for your-own)
    - 1 primary private IPv4 CIDR block
        - optional secondary IPv4 block
        - optional single assigned IPv6 /56 CIDR block
    - subnet
        - 200 subnet per VPC
        - 1 subnet ⇒ 1 AZ, 1 AZ ⇒ ≥0 subset
        - IPv4 CIDR is a subset of the VPC CIDR
        - subnets can communicate with other subnets in the VPC
        - Every subnet have 5 reserved IP not for customized use:
            - eg 10.16.16.0/20 (10.16.16.0 ⇒ 10.16.31.255). These 5 would be
                - Network address (10.16.16.0)
                - ‘Network +1’ (10.16.16.1) - VPC router (move data between subnets)
                - ‘Network +2’ (10.16.16.2) - reserved for possible DNS
                - ‘Network +3’ (10.16.16.3) - reserved future use
                - Broadcast Address 10.16.31.255 (last IP in subnet)
        - VPC has a DHCP options set that received IP addresses that flows through to subnet, controlling DNS servers, NTP servers….
        - two important allocation option
            1. auto assign Public IPv4
            2. auto assign Public IPv6
- **Components**

    [[VPC/Untitled.png]]


**Basic**

- **VPC router**
    - every VPC has a VPC router that routes traffic between subnets
    - in every subnet ‘network+1’ address
    - controlled by ‘route tables’ each subnet has one
- **Route Tables**
    - directed the network traffic
    - a VPC has a Main route table as default, which used by all subnet
    - **each subnet must have a route table**, route table can associate with multiple subnet
    - subnet can associate with its own route table, but it will disassociate with the Main route table
    - higher the number of prefix in address = more specific = higher priority
    - **Destination**—The range of IP addresses where you want traffic to go
    - **Target**—The gateway, network interface, or connection through which to send the destination traffic; for example, an internet gateway.
- **Internet Gateway (IGW)**
    - Two Function:
        1. provide a target in your VPC route table for internet-routable traffic
        2. perform NAT for instances that have been assigned public IPv4
    - runs from within the AWS public zone, traffic between VPC and internet/ AWS public zone
    - regionally resilient. 1 gate cover all VPC across AZs. Each VPC will have ≥0 gateway
    - maintain the allocated public IP of the resource (eg EC2), and direct to the resource private ID. The **public ID actually doesn’t touch any resource/OS instance directly**
- **Design Consideration**
    - what size
    - cloud, on-premises, partners & vendors
    - predict the future
    - VPC structure - tiers & resiliency (availability) zones
    - network
        - how many networks>subnet>ip address needed?
        - any networks we can’t use that need to avoid?
        - good to reserve 2+ networks per region being used per account
        - good to have 10.x.y.z range
    - Good to have 4 subset = 4 regions = 3 for resilient, 1 for future spare
- **bastion/ jump-box**
    - instance in a public subnet to allow incoming management connections arrive there, then access internal VPC resources
    - use it if a VPC is highly secure and provide the only entry point to access the VPC

**Security**

- **stateful vs stateless firewall**
    - stateless
        - doesn’t understand state of connection (what’s request and what’s response)
        - request & response needs two rules for each inbound or outbound connection
        - need allow TCP443 to accept the request and a full range of ephemeral ports for sending response
    - stateful
        - can identify request & response
        - only have to allow request or not, and the response will be allow or not automatically
        - reduce admin overhead
- **Network Access Control List (NACL) - stateless/ subnet level**
    - connections within a subnet aren’t impacted by NACLs
    - every subnet has an associated NACL, filtering traffic across the subnet boundary inbound/ outbound, **each need a corresponding rules for explicit allow/deny**
    - **rules are processed in order**, lowest rule number first
        - match occurs, rule apply, stop processing.
    - default NACLs after creating VPC come with everything being **allowed**
    - custom NACLs are initially associated with no subnets
        - only have 1 inbound/ outbound come with everything being **deny**
    - only IPs/CIDR, ports & protocols - no logical resources
    - cannot be assigned to AWS resources - only subnets
    - each subnet can have only one NACL, a NACL can be associated with many subnets
    - NACL mainly responsible for deny, while working with SGs which allow

    [[VPC/Untitled 1.png]]

    Optional layer of virtual firewall at the subnet level

    [[VPC/Untitled 2.png]]

    [[VPC/Untitled 3.png]]

- **Security Groups - stateful/ instance level**

    Virtual firewall at the instance level

    - no explicit deny, only explicit allow, can’t block specific bad actors because it cannot deny a specific IPs
    - Supports IP/CIDR
    - SGs of one resource can references **logical resources with a existing SGs:**
        - easy to scale
        - no need to care the IP/CIDR
        - self-references possible = anything with this SG attach = attach everythings
    - attached to ENI’s not instances (even if the UI show it this way)

    [[VPC/Untitled 4.png]]

    [[VPC/Untitled 5.png]]

    [[VPC/Untitled 6.png]]

    [[VPC/Untitled 7.png]]


**Connectivity**

- **Network Address Translation (NAT)** for each subnet
    - runs from a public subnet connecting to the IGW
    - use elastic IPs
    - **NAT don’t work with IPv6**, all IPv6 address in AWS are publicly routable
    - AZ resilient service, each AW need 1 NAT gateway
    - set of different process which can adject IP packets by remapping their source or destination IP address
    - **IP masquerading:** hiding whole private CIDR blocks behind one public IP = NAT is an agent help the speak out to outer world without exposing their identity!
    - why?
        - **Outbound-only traffic:** allows outbound internet connectivity for resources within private subnets while preventing inbound traffic
        - **Source IP preservation:** public IP address associated with the NAT Gateway is used as the source IP address for communication instead of the assigned instance IP
        - **Scalability:** handle increasing outbound traffic loads without having to manually provision or manage the infrastructure
    - Two ways provide NAT service
        - NAT gateway (most of the time/ most optimal)
        - NAT instances (cheaper if your volume is small/ can be also use as a normal EC2)

    [[VPC/Untitled 8.png]]

    [[VPC/Untitled 9.png]]

- **VPC Flow Logs**

    [[VPC/Untitled 10.png]]

    - monitor traffic of ENI within your VPC, in 3 level:
        - all ENIs in a VPC
        - all ENIs in a subnet
        - ENIs directly
    - only capture **accepted/ rejected/ all metadata** (no contents), **not real-time**
    - request & response (network ACL are stateless) evaluated separately = 2 row
    - Stored in **Cloudwatch log** or **S3**, **athena** for querying
    - not logged
        - AWS DNS servers, 169.254.169.254, DHCP, window license activation traffic
- **Egress-only internet gateway**
    - NAT allows private IPv4s to access public networks (in-out),. **without allowing externally initiated connections** (not out-in)
    - However, IPv6 can always be free both in- and out-bound. Nat cannot be used
    - Egress-only is outbound-only for IPv6, architecturally same as normal
        - the default IPv6 route **::/0** added to RT with **eigw-id** as **target**
        - response can be sent back from our request, but not request from the outer world
- **VPC Endpoints**
    - allow you to privately connect your VPC to other AWS services
    - No NAT needed (because no public connection)
    - not accessible outside the VPC
    - endpoint policy is used to control what it can done (eg access specific bucket in S3)
    - 1. **Gateway endpoint (free)**

        [[VPC/Untitled 11.png]]

        - provide **private access** to only **S3** and **dynamoDB** via **routing**
        - **HA across all AZs in a region**, just associated subnets to it. but **can’t access cross-region services**
        - **prefix list** is automatically added to route table to the subnet when you allocated the gateway endpoint to the subnet, which **use gateway endpoint as target**
        - **prevent leaky buckets**: set the S3 bucket as private by allowing access from only gateway endpoint
    - 2. **Interface endpoint (cost)**

        [[VPC/Untitled 12.png]]

        - provide **private access** to **many AWS services** (no dynamoDB) via **new DNS**
        - **use ENI with private IPs**
            - Endpoint provides a **new service** **endpoint DNS** and instances use it to access other services
            - applications can optionally use default **regional DNS & zonal DNS**, or
            - **privateDNS overrides** the **default DNS** for services (privateDNS = DNS associated a route 53 private hosted zone with your VPC)
        - **powered by AWS privateLINK**
            - allow external services to be injected into your VPC either from AWS/ 3rd parties
            - good for working in a heavily regulated industry, but want to provide access to 3rd services inside private VPCs without building extra infrastructure
        - added to specific subnets - an ENI - not HA
            - for HA.. add 1 **endpoint** to 1 **subnet**, per AZ used in the VPC
            - use **security groups** to control access to the interface endpoint
            - **TCP & IPv4 only**
- **VPC peering**
    - create a private 7 **encrypted** network route link between **two VPCs (no more than two)**, using private IP
    - instances on peered VPCs behave just like they are on the same network
        - same regions SG’s can reference peer SGs
    - **works same/ corss-region & same/ cross-account**
    - (optional) public hostnames resolve to private IPs
    - configuration steps
        1. peer connection
        2. routing
        3. allow traffic to flow via **SGs (**stateful**) & NACLs**
    - **not support transitive peering (A-B & B-C ≠ A-C )**
    - **VPC CIDR cannot overlap**

    [[VPC/Untitled 13.png]]
