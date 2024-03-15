# AWS Transfer Family

[[AWS Transfer Family/Untitled.png]]

- managed file transfer service that supports transferring TO/FROM **S3 & EFS**
- provide managed “**servers**” which support many **protocols**
    - **File transfer protocol (FTP)** - unencrypted file transfer
    - **File transfer protocol secure (FTPS)** - File transfer with TLS encryption
    - **SSH File Transfer protocol (SFTP)** - file transfer over SSH
    - **Applicability statement 2 (AS2)** - structured B2B data
- when you need to interact with S3/ EFS while not able to change the application
    - use existing workflow or
    - managed file transfer workflows (MFTW) - serverless file workflow engine
- Identities - service managed, directory service, custom (Lambda/ APIGW)
- multi-AZ
- $$ server per hour + data transferred
- **Endpoint type**

    [[AWS Transfer Family/Untitled 1.png]]
