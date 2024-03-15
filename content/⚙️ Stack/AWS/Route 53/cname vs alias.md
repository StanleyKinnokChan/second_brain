# cname vs alias

cname

- “A” maps a name to an IP address (eg [cat.io](http://cat.io) maps to 1.3.3.7)
- CNAME maps a NAME to another NAME (www.cat.io ⇒ cat.io), create alternative name for something within DNS
- However, CNAME is invalid for naked domain (cannot cat.io⇒ www.cat.io)
- many AWS services use a DNS name, cannot point to a CNAME

alias

- only used when route 53 hosting the domain, it is not a DNS standard
- ALIAS records map a name to an AWS resource
- can be used both for naked and normal records
- For AWS services - default to picking ALIS
