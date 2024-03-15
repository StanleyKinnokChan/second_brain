# DeletionPolicy

- by default, physical resource is deleted after the logical resource from a template is deleted
- only applies to deletion operation of logical resource….not to replacement/changes
- With deletion policy, you can define on each resource to…..
    - delete (default)
    - retain
    - snapshot (if supported; EBS volume, elasticache, EDS, redshift), have to clean up because it will continue to incur storage cost

[[DeletionPolicy/Untitled.png]]
