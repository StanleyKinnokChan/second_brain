# AWS Direct Connect (DX)

- Dedicated private connection from an on-premise data center to a VPC
- a physical connection (1/10/100 Gbps) links your internal network to an AWS Direct Connect location over a standard Ethernet fiber-optic cable
- More stable and secure than Site-to-Site VPN
- Access public & private resources on the same connection using **Public & Private Virtual Interface (VIF)** respectively
- with IPsec running over a direct connect as encryption
- it is a port allocation at a DX location
- billing ⇒ port hourly cost & outbound data transfer
- requires **long provisioning time** for physical able & no resilience
- low & consistent latency + high speeds + high throughtput
- architecture

[[AWS Direct Connect (DX]]%20c5aaf52bf51e4eeb90de215e19c23904/Untitled.png)

- **Resilience and HA**
    - single point of failure
        - DX location
        - DX router
        - Cross connect
        - Customer DX router
        - Extension
        - Customer premises
        - Customer Router

    [[AWS Direct Connect (DX]]%20c5aaf52bf51e4eeb90de215e19c23904/Untitled%201.png)

    - Improvement evolution1
        - independent & multiple router + connection

            [[AWS Direct Connect (DX]]%20c5aaf52bf51e4eeb90de215e19c23904/Untitled%202.png)

    - Improvement evolution2

        [[AWS Direct Connect (DX]]%20c5aaf52bf51e4eeb90de215e19c23904/Untitled%203.png)

    - Improvement evolution3

        [[AWS Direct Connect (DX]]%20c5aaf52bf51e4eeb90de215e19c23904/Untitled%204.png)


- **public (virtual interface)VIF + IPsec VPN**
    - **encrypted** & **authenticated** tunnel over **DX**
    - public VIF alone doesn’t offer any form of encryption
    - transit agnostic (DX/ public internet)
        - method of data transmission is irrelevant to the device or program's function
        - can connect over public internet/ public VIF, VPN config are the same
        - Wide vendor support
        - more cryptographic overhead which limits speeds
        - can be used while DX is being provisioned/ as a DX backup


.
