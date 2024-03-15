# Scaling

**Vertical Scaling**

- resizing an instance
- each resize requires a reboot - disruption
- larger instances often carry a premium
- upper cap on performance - instance size
- no application modification
- works for all applications even monoliths

**Horizonal Scaling**

- add more instances
- **Sessions** are everything
    - requires external application support (load balancer is needed)/ off-host sessions (info out of servers)
- no disruption when scaling
- no real limit
- less expensive
