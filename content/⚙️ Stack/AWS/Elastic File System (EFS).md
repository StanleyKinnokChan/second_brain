# Elastic File System (EFS)

[[Elastic File System (EFS]]%205d784c955e8b4d3c8f47dcd40fbfd49a/Untitled.png)

- use Network File Sharing (NFS) as protocol, for Linux only
- EFS is an implementation of NFSv4
- EFS **filesystems** can be **mounted in Linux**
- **Shared** between many EC2 instances
- private service, via **mount targets** inside a VPC
- accessible from on-premises - VPN or DX with POSIX permissions
- General purpose & Max I/O performance modes
- bursting and provisioned throughput modes
- standard & infrequent access classes
- lifecycle policy can be used with class
