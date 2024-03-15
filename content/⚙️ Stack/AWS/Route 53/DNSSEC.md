# DNSSEC

- creates a secure domain name system by adding cryptographic signatures to existing DNS record

[[DNSSEC/Untitled.png]]

- **Key-Signing Keys (**KSK) key is regional specific generated from KMS
- R53 generate and manage **Zone-Signing Keys** (ZSK) internally
- R53 adds KSK and ZSK public part into a **DNSKEY** record within hosted key, telling any DNSSEC resolvers which public keys to use to verify the signature
- private KSK is used to sign those DNSKEY records create the RRSIG DNSKEY record
