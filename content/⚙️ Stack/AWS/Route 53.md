# Route 53

**Overall:**

- Global Resilient service with single database of DSN records (hosted host)
- **2 services**
    - **1. register domain names**
    - **2. Host zones managed nameservers**
- host zone = database for the DSN records, which was allocated 4 different name server to host the zone, the referred DSN authoritative for a domain (.org,.io…)
- send back IP when users make a DSN. The IP was then sent to the server communication under HTTP
- can be public or private (VPC linked)
- registry maintains the zones for a Top-Level Domain (TLD)
- Registrar has relationships with the .org TLD zone manager allowing domain registration

[[DNS records types]]

[[Public hosted zones]]

[[Private Hosted zones]]

[[cname vs alias]]

[[Routing Policies]]

[[Health checks]]

[Interoperability (work with 3rd party)](Route%2053%209caf0bcc7a0742048ef646d629f57ac7/Interoperability%20(work%20with%203rd%20party)%207c006c98cab146d09aa9136f9860203f.md)

[[DNSSEC]]
