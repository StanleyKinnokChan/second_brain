# Firewalls (Layer 3/4/5 vs Layer 7)

[[Firewalls (Layer 3 4 5 vs Layer 7]]%2040a3f87e6b2c421fb366a00ee98a5391/Untitled.png)

- layer 3/4 deals with networking and managing the request and response (upper), layer 5 added session (lower)
- Neither of them can see headers/ any of other data being transferred over HTTP. It suffers from a wide range of attack

[[Firewalls (Layer 3 4 5 vs Layer 7]]%2040a3f87e6b2c421fb366a00ee98a5391/Untitled%201.png)

- layer 7 firewall stripped off the SSL (HTTPS→HTTP) and understand the data, then block the bad one and re-establish a new HTTPS delivered to the endpoint
- could be protocol specific
