# AWS Certificate Manager (ACM)

<aside>
💡 Use **AWS Certificate Manager** (ACM) to provision, manage, and deploy public and private SSL/TLS certificates for use with AWS services and your internal connected resources. ACM removes the time-consuming manual process of purchasing, uploading, and renewing SSL/TLS certificates.

</aside>

[[AWS Certificate Manager (ACM]]%20d0a3994f93fe41c58da9e9091c0bb9de/product-page-diagram_AWS-Certificate_Manager2x.7b2b51b8a698ccac2bbe4d1d904a8ef501dcdda4.png)

- HTTPS - SSL/TLS layer of encryption added to HTTP, data is encrypted in-transit
- certificates prove identity, which is provided by a trusted authority by identifying DNS name
    - a chain of trust is formed: web client trusts the authority, you trust the cert. which it signs

[[AWS Certificate Manager (ACM]]%20d0a3994f93fe41c58da9e9091c0bb9de/Untitled.png)

- ACM lets you run a public or private certificate authority (CA)
    - **public CA** - browsers trust a list of providers, which can trust other providers
    - **private CA** - applications need to trust your private CA, adding policy to configure the trust
- ACM can generate or import cert.
    - **if generated…it can automatically renew**
    - **if imported…you are responsible for renewal**
- **cert can be deployed out, to supported AWS services only (cloudfront & ALBs…not EC2)**
- ACM is a **regional service**, **cert cannot leave** the region they are generated or imported in
    - where you need cert, generate/import the cert in there
    - for global services, operate as though within ‘us-east-1’
