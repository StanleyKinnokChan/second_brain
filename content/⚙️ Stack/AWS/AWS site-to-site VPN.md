# AWS site-to-site VPN

<aside>
💡 **AWS Site-to-Site VPN** is a fully-managed service that creates a secure connection between your data center or branch office and your AWS resources using IP Security (IPSec) tunnels. When using Site-to-Site VPN, you can connect to both your Amazon Virtual Private Clouds (VPC) as well as AWS Transit Gateway, and two tunnels per connection are used for increased redundancy.

</aside>

- logical connection between VPC and on-premises network encrypted using IPSec, running over the public internet
- HA - multiple endpoints and multiple tunnels
- quick to provision (<1hr)
- component
    - Virtual private Gateway (VGW)
    - Customer gateway (CGW) - be it logical or physical, created by you
    - VPN connection between VGW and CGW

    [[AWS site-to-site VPN/Untitled.png]]

    *lock = VPN


**Static vs dynamic VPN (BGP)**

[[AWS site-to-site VPN/Untitled 1.png]]

- static
    - just use IPSEC for simple connect
- dynamic
    - use BGP support load balancing, multi-connection failover


**AWS VPN consideration**

- speed limitation ~1.25 Gbps
- latency - inconsistent, public internet ⇒ alternative is direct connect
- cost - hourly cost, GB out cost, data cap
- speed of setup - hours for all software configuration
- can be used with direct connect
