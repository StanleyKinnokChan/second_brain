# Border Gateway protocol (BGP)101

<aside>
💡 **Border Gateway Protocol** (BGP) is a standardized exterior gateway protocol designed to exchange routing and reachability information among autonomous systems (AS) on the Internet.

</aside>

[[Border Gateway protocol (BGP]]101%2044720ad38c2e48fe8a44ac46c6bd406a/Untitled.png)

- protocol used to control how data flows
- make up of a lot of self-managed system called autonomous system (AS)
    - collection of routers/ network controlled by one entity ⇒ like a blackbox
    - each is allocated an **autonomous system number (ASN)** by IANA. 64512-65534 are private, used by BGP to distinguish network
- BGP operates over a tcp/179, but not automatic, peering is manually configured
- BGP is a **path-vector** protocol = exchanges the best path to destination between peers. The path is called the **ASPATH**
- direct connect & dynamic VPN use BGP
- AS PATH prepending: set up the path to be longer than it was (must pass through certain AS PATH) and make that AS system select another desired path
