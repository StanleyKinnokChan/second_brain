# CloudHSM

- KMS is a shared service that other acc also use, AWS also has certain level of access to KMS service
- **hardware security module** (HSM) industry standard hardware to manage keys and perform cryptographic operation, which is also used by KMS service
- provide true single tenant HSM **hosted within AWS cloud provisioned by AWS** and **managed by customer** (AWS has no access)
- compliance **fully FIPS 140-2 lvl3** (lvl2 for KMS)
- **access by industry standard APIs** - PKCS#11, JCE, CNG libraries
- KMS can use cloudHSM as a custom key store (integration)

**Architecture**

[[CloudHSM/Untitled.png]]

- not deploy with in customer VPC, but AWS managed cloud HSM VPC
- HSM itself is not HA, but run multiple as cluster
- the cluster injected to the customer VPC via ENI, then the services inside the customer VPC can utilize the HSM cluster by using these ENI
- also use LB for HA
- a client needs to be installed on the ec2 instances for accessing the cloudHSM, then accessing via API

**How it differ from KMS?**

- AWS have **no access to the data**
- **NO native AWS integration** eg S3 SSE
- can be used to offload the SSL/TLS processing for web servers
- enable **transparent data encryption (TDE)** for oracle databases
- protect the private keys for an issuing certificate authority
