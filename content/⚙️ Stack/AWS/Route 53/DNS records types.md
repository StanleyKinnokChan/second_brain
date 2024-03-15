# DNS records types

- Nameserver (NS; subdomain)
    - directs to name servers
- A and AAAA records: convert host name to IP
    - A: IPv4
    - AAAA: IPv6
- CNAME records (alias)
    - direct one name to another name (eg [gmail.com](http://gmail.com) → mail.google.com)
    - ftp, mail, www all linked with single name
- MX (mail exchanger) records
    - consist of priority and value
    - find the server where your IP located with a priority of server
- TXT records
    - add arbitrary text to a domain for some usage
    - The most commonly used DNS record type to verify domain ownership is the "TXT" (text) record. TXT records are typically used to store any text-based information associated with a domain. When verifying domain ownership, a DNS TXT record is often created with a specific value provided by the domain registrar or service provider. This value is used as a verification token or proof of ownership during the domain verification process.
    - eg add the owner name so other can know extra-info

TTL - Time To Live

- the time in second the data stored in a computer or network
