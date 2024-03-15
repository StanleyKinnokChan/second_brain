# Web Application Firewall (WAF)

[Firewalls (Layer 3/4/5 vs Layer 7)](Web%20Application%20Firewall%20(WAF)%208fd2e450dbe24d94831008c561202152/Firewalls%20(Layer%203%204%205%20vs%20Layer%207)%2040a3f87e6b2c421fb366a00ee98a5391.md)

[[Web Application Firewall (WAF]]%208fd2e450dbe24d94831008c561202152/Untitled.png)

- layer 7 firewall prevent layer 7 attacks, SQL injection & cross-site scripting
- can be added to CloudFront, APIGateway, ALB
- WAF > WEBACL > rule group > rules
- can do automated things like event bridge and scheduled rules to allow/deny lists of IP
- logs can be recorded and go to S3, and update the firewall based on the record as well **(a feedback loop)**
- **monthly price** per web ACL & rule & requests per WEBACL, plus optional intelligent threat mitigation/ captcha/ fraud control/ marketplace rule group

**WEBACL (Web access control list)**

- is used to associate with other supported services and control the access
- **default action** (ALLOW/ BLOCK)
- is created for Cloudfront/ regional service
- add rule groups/ rules - processed in order
- limited by a computing unit ⇒ WCU (capacity unites; default is 1500), can be increased via support tickets
- adjusting a WEBACL takes less time than associating one

**Rule groups**

- groups contain rules
- don’t have default actions. That’s defined when groups/ rules are added to WEBACLs
- managed by AWS, yours or service owned (shield/ firewall manager)
- can be referenced by multiple WEBACL
- have a WCU

**Rules**

- **type**, **statement**, **action** (how it work, how to match, what action to take)
    - **Type**: regular/ rate-based (=possible attack)
    - **statement**:
        - what/ connection count/ Both
        - country, IP, header, cookies, URL path, HTTP method, body (**only first 8192 bytes**)…..
        - single, and, or, not condition
    - **Action**: allow (not for rate-based), block, count, captcha, custom response (eg header), add label for following up
- if rule is matched, no further actions (allow/block) are taken but count/ capture keep processing, of which the behaviour can be controlled with label
