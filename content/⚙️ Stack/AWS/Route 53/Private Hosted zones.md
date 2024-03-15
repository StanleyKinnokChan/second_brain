# Private Hosted zones

- associated with VPCs and only accessible in those VPCs
- using different accounts is supported via CLI/API

[[Private Hosted zones/Untitled.png]]

- **Split horizon DNS** (DNS overlapping public & private) for both public and internet use with the same zone name
    - public only access a subset of these resources records
    - same domain, different accessibility to resources records between public and private

[[Private Hosted zones/Untitled 1.png]]
