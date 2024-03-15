# IPSec VPN fundamentals

- IPSEC VPN is a group of protocol setting up **secure tunnels** across **insecure public networks** between **two peers** (local & remote) on layer 3
- provides **authentication** & **encryption** (ciphertext)
- If data matches any of rules, it’s classified as interesting traffic, then VPN tunnel was created and deliver the data.

<aside>
💡 **Interesting traffic** is literally the traffic you are interested in for a particular reason. It is allowed in the encryption domain

</aside>

- two phase
    1. IKE phase 1 (slow & heavy)
        - authenticate with pre-shared key (pw)/ certificate
        - using asymmetric encryption to agree on, and create a shared symmetric key (diffie-hellman exchange)
        - phase 1 tunnel (IKE SA) is created
    2. IKE phase 2 (fast & agile)
        - use keys agree in phase 1 create phase 2 tunnel (IPSEC security association (***SA***))


Policy-base VPNs

- created rules sets match traffic ⇒ a pair of SAs

Route-based VPNs

- target matching (prefix) ⇒ match a pair of SAs
