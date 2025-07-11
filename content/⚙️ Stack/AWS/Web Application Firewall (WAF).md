# Web Application Firewall (WAF)


- layer 7 firewall prevent layer 7 attacks, SQL injection & cross-site scripting
- doesn't support NLB
- can be added to CloudFront, APIGateway, ALB, application load balancer
- WAF > WEBACL > rule group > rules
- can do automated things like event bridge and scheduled rules to allow/deny lists of IP
- logs can be recorded and go to S3, and update the firewall based on the record as well **(a feedback loop)**
- **monthly price** per web ACL & rule & requests per WEBACL, plus optional intelligent threat mitigation/ captcha/ fraud control/ marketplace rule group

**WEBACL (Web access control list)**

- is used to associate with other supported services and control the access
- **default action** (ALLOW/ BLOCK)
- is created for Cloudfront/ regional service
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

Application load balancer (ALB)
- we can attached WAF to ALB
- as application load balancer doesn't have a fixed IP, we connect Global accelerator to it so user can go in global accelrator and reach the ALB