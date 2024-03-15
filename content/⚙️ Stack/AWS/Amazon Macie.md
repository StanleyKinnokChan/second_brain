# Amazon Macie

[[Amazon Macie/Untitled.png]]

- data security & privacy service, classifying the data as private/ sensitive
- discover, monitor & protect data… stored in S3 buckets
- **automated discovery** of sensitive data (PII, PHI, finance)
- ma**naged data identifiers** - built-in - ML/patterns
    - growing list of common sensitive data types
        - credential, finance, personal ID….
- **custom data identifiers** - proprietary - regex based
    - regex pattern, keywords, ignore words, max. match distance
- integrates with security hub & evenbridge
- centrally manage.. either via AWS ORG/ one Macie account inviting

**Findings**

- policy findings
    - when policies or settings for S3 bucket are changed in a way that reduces the security
    - eg S3BlockPublicAccessDisabled, S3BucketEncryptionDisabled
- sensitive findings
    - eg S3Object/Credentials, S3Object/Financial,S3Object/Personal
