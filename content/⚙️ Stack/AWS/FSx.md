# FSx

EFS ⇒ linux ; FSx ⇒ window

- For windows file server

    [[FSx/Untitled.png]]

    - provides a fully managed **native windows file server**
    - designed for **integration with windows env** (and window permission model**)**
    - **integrates with directory service/ self-managed AD**
    - single or multi-AZ within a VPC
    - **VSS** - file/ folder level restore from previous version (user-driven)
    - support **Distributed file system (DFS)** - scale-out file share structure
    - allows **on-demand/ scheduled backups**
    - accessible using VPC, peering, VPC, direct Connect
    - share via **SMB protocol**

- For Lustre

    <aside>
    💡 **Lustre** is a type of parallel distributed file system, generally used for large-scale cluster computing for Linux, which designed for HPC

    </aside>

    [[FSx/Untitled 1.png]]

    - support **Linux** and **POXIS** style permission
    - for ML, big data, financial modelling
    - accessible over VPN or Direct connect
    - S3 as file repository from which file is lazy loaded into FSX when needed

        [[FSx/Untitled 2.png]]

    - can backup back to S3
    - Two deployment type
        - Scratch
            - highly optimised for short term workloads
            - for pure performance w/o replication/ any HA
            - larger file system = more change of failure
        - Persistent:
            - longer term
            - replication within 1 AZ, self-healing
