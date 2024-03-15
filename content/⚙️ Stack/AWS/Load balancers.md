# Load balancers

**Architecture**

[[Load balancers/Untitled.png]]

- is a DNS A record pointing at ≥ 1 nodes per AZ, load balancer node is created in each specified subnet. The nodes can scale
- need to choose between
    - internet facing (provide public+private IPv4IPs)
    - internal (only private IPs)
- EC2 doesn’t need to be public to work with a LB
- DNS name resolves to the nodes
- listener configuration control what the node does (to accept what protocol and port)
- /27 subnet is normally considered as minimum to deploy load balancer and allow scaling

Multi-tier ELB

[[Load balancers/Untitled 1.png]]

- allow the resources to grow
- client won’t know which one he is using
- the load balancer is aware of each other

**Cross-zone LB**

[[Load balancers/Untitled 2.png]]

- LB split it 50/50%, but instance in AZB will receive too much load
- cross-zone LB allows the load distribute across the AZs

**2 types of LB:**

- **Application load balancer (ALB)** - HTTP/ WebSocket
    - layer 7 load balancers, no other layer 7 protocols (SMTP, SSH, gaming)
    - no TCP/ UDP/ TLS listeners
    - understand L7 content: cookies, custom headers, user location, app behaviour
    - HTTP HTTPS always terminated on the ALB and a new connection is made to the application
    - ALBs Must have SSL certs if HTTPs is used
    - slower than NLB as more LV of network stack to process
    - can health checks evaluate application health
    - Rules
        - direct connections which arrive at a listener
        - processed in priority order
        - default rule = catchall
        - can take rule conditions
        - actions: forward, redirect, fixed-response, authenticate-oids & authenticate-cognito
- **Network load balancer (NLB)** - TCP, TLS & UDP
    - Layer 4 load balancers, TCP, TLS, UDP, TCP_UDP
    - no visibility or understanding of HTTP/ HTTPS
    - no header, cookies, session stickiness
    - crazily fast (handling 1milllions request/s)
    - SMTP, SSH, game servers, financial apps
    - health checks just check ICMP/ TCP
    - NLB can have **static IP’s** - useful for whitelisting
    - forward TCP to instances with unbroken encryption

**ALB or NLB**

[[Load balancers/Untitled 3.png]]

**Three way of ELB can handle secure handle:**

[[Load balancers/Untitled 4.png]]

1. Bridging
    - AWS have some level of access to the certification
    - re-encrypted HTTP within a wrapper and send to EC2, then cryptographic operation is done by EC2
    - Pro: ELB can get to see the unencrypted HTTP and take action based on the text
    - Con: cert store on ELB which is risky, admin overhead and intense cryptographic operation

.2. Pass-through

- never touch the encryption, AWS won’t see the cert.
1. Offload
    - data is encrypted between client and ELB, but not between ELB & EC2
    - fast and low workload of EC2 (no cryptographic operation)

**Connection stickiness**

[[Load balancers/Untitled 5.png]]

- Without stickiness, every time the user access the site he is directed to a new instance (open a new session)
- With stickiness, the session was maintained in a time frame and the user was direct to same instance (same session) → not efficient for load balancing
- Broken if one of two things occurs:
    - EC2 server failure - move to new EC2
    - cookie expired - new session
- can cause uneven load on back end servers
    - solution: holding session/ user state externally (eg dynamoDB) so that EC2 is stateless
    - then LB can be performed automatically without using cookies


**Gateway Load Balancers (GWLB)**

[[Load balancers/Untitled 6.png]]

- run and scale 3rd party application (eg firewalls, intrusion detection, prevention)
- mainly for network security at scale
- both inbound & outbound traffic
- 2 major component
    - GWLB endpoints from a VPC (where traffic enters/ leaves)
    - GWLB balances across multiple backend appliances
- use **GENEVE** protocol (a tunnel is created between the gateway load balancer & backend instances)
