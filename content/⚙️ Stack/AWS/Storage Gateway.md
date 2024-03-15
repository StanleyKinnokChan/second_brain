# Storage Gateway

<aside>
💡 **AWS Storage Gateway** is a set of hybrid cloud storage services that provide on-premises access to virtually unlimited cloud storage.

</aside>

- commonly used in virtual machine
- **via storage gateway endpoint**
- network-attached storage (NAS) to present storage using iSCSI/ NFS/ SMB protocols

<aside>
💡 iSCSI is a Block level based sharing on window
SMB is a File-Based sharing on window/ linux
NFS is a File-Based sharing on linux

</aside>

- integrates with EBS, S3, glacier within AWS
- for migrations, extensions, storage tiering, DR and replacement of backups systems

- Volume store mode

    [[Storage Gateway/Untitled.png]]

    - **‘create a copied to AWS’**
    - cloud-based iSCSI block storage volume
    - In gateway store mode, gateway VM has local storage. Volumes consume capacity on premises
    - Data also is written to the upload buffer temporarily and copied asynchronously to S3 in form of EBS snapshot
    - good for doing **full-disk backup** (nice RTO RPO, low latency)
    - Entire dataset is stored in AWS and on-prem
    - doesn’t improve data center capacity, main copy of data is store on the gateway
- Volume Cache Mode

    [[Storage Gateway/Untitled 1.png]]

    - **‘AWS as a primary storage as a main infrastructure’**
    - cloud-based iSCSI block storage volume
    - **catch locally** and data store in primary storage S3
    - can use the storage in S3 to create EBS snapshots
    - frequently accessed data is stored on-prem
    - allow data center extension to AWS
- Tape/VTL Mode
    - replace using physical tapes on premises with virtual tapes in AWS without changing existing backup workflows
    - large backups ⇒ tape
        - highly compressed
        - read at a time, write at a time
        - required Loader that move tape in library
        - drive < library < shelf
    - traditional

    [[Storage Gateway/Untitled 2.png]]

    - problems solved by VTL mode
        - pretend to be an iSCSI tape library, changer & drive
        - use virtual tape and use S3 and glacier as library and shelf

        [[Storage Gateway/Untitled 3.png]]

- File Mode
    - **links on-premises file storage & S3**
        - **S3 object visible in file system & vice versa**
        - combine with S3 classes & life cycle
    - mount points available via **NFS/ SMB**
    - on-premises files map directly onto an **S3 bucket**
    - **files stored** into a **mount point**, are **visible as objects** in an **S3 bucket**
    - read & write caching ensure LAN-like performance
    - can be ≥2-sites architecture; one upload, all site will change
    - can directly access the volume

        [[Storage Gateway/Untitled 4.png]]

        [[Storage Gateway/Untitled 5.png]]
