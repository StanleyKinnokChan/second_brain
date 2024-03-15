# Elastic Container Registry (ECR)

- **Container image registry service** managed by AWS (like docker)
- each AWS account has a public and private registry
    - Public: anyone can pull, R/W requires permissions
    - Private: permissions required for both pulling/ R/W
- Each registry can have many repositories
    - Each repository can contain many images
        - Each images can have several tags
- integrated with IAM for permissions
- Image scanning
    - basic
    - enhanced
- offer near real-time metrics ⇒ auth, push, pull
- log API actions into cloudtrail
- can generates events delivered to EventBridge
- replication available for cross-region and cross-account
