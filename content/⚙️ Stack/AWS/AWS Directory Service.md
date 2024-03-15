# AWS Directory Service

**Directory**

- directory stores objects (users, groups, computers, servers, file share with a structure) allowing centralized management
- multiple tress can be grouped into a forest
- commonly used in windows env.

**Directory Service**

- runs within a VPC
- provide HA by deploying multiple subnet & AZs
- some WAS services need a directory (eg Amazon Workspaces)
- Three modes
    1. **Simple Active Directory(AD) mode**
        - isolated
        - no integration

        [[AWS Directory Service/Untitled.png]]

    2. **AWS managed Microsoft AD**
        - integrated with existing on-premise system
        - when you want a direct presence inside AWS, but also have an existing on-premise env ⇒ allow integration
        - create trust relationship with on-premises directory via direct connect/ VPN
        - directly supported other application that required Microsoft AD (Sharepoint, SQL server..)

        [[AWS Directory Service/Untitled 1.png]]

    3. **AD connector**
        - as a proxy back to on-premises
        - only want to use an AWS service that need AD, have on-premises directory but no AWS AD, use this to connect both via VPN

        [[AWS Directory Service/Untitled 2.png]]
