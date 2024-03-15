# AWS Shield

- protect any internet-connected environment
- protect 3 types of DDOS attack
    1. Network volumetric attacks (L3) - saturate capacity (server overwhelmed)
    2. Network protocol attacks (L4) - TCP SYN flood (occupied all connection port with dummy)
    3. application layer attacks (L7) - web request floods (huge request *n, server need very long time to process 1 request)
    - 2 forms for DDOS protection
        - Standard (free)
            - protect the perimeter of the network (eg. region/ VPC/ AWS edge)
            - Common network (L3)/ transport(L4) layer attacks
            - best protection using R53, cloudFront, global accelerator
        - Advanced (very cost. commercial level)
            - anything associated with EIPs (ie EC2), ALBs, CLBs, NLBs
            - not automatic, must be explicitly enabled in Shield advanced or AWS firewall manager shield advanced policy
            - able to integration with the WAF to implement its protection against L7 attack
            - Benefit:
                - **cost protection** for unmitigated attack
                - proactive engagement from **AWS shield response team** (SRT) with trouble shoot/ possible attack detection
                - **protection group**
                    - grouping of resources protected by shield
                    - can defined the criteria of membership so that the newly created resource will be automatically included in the group
                    - reduce admin overhead
                - **real time metrics** of DDOS events and attacks
            - **application specific health check** have to be enable for proactive engagement team
