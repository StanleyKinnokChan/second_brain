# Routing Policies

**Simple routing**

[[Routing Policies/Untitled.png]]

- No health check, all send to client for their choice

**Failover routing**

[[Routing Policies/Untitled 1.png]]

- if a health check pass, use the primary record as normal
- if a health check fails, direct to secondary record for a failure page

**Multi value routing**

[[Routing Policies/Untitled 2.png]]

- return all healthy record and send to client for their choice

**Weighted routing**

[[Routing Policies/Untitled 3.png]]

- Specified the record weight, total weight is calculated (40+40+20=100)
- the frequency of records returns as the specified weight
- unhealth = skipped, but the weight won’t change
- good for load balancing or testing new software versions

**Latency-Based routing**

[[Routing Policies/Untitled 4.png]]

- send the lowest latency to users
- if one’s health check fail, move to 2nd lowest latency

**Geolocation routing**

[[Routing Policies/Untitled 5.png]]

- IP check verifies the location of the user and return the matched location
- check state > country > continent >  ‘no answer’
- can be used for regional restrictions and geographical load balancing
- **NOT THE CLOSEST RECORDS**

**Geo-proximity routing**

[[Routing Policies/Untitled 6.png]]

- you defined regional rules
- direct the records to the closest recourse
- introduce **“+”/ “-” bias for** certain counties that change the calculation, so more or less resources were routed to those countries
