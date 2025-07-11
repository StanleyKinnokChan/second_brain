# Amazon DataZone

- Data management service
	- Facilitates cataloging, discovering, sharing, and governing data
- Supports
	- AWS
	- On-Premises data
	- Third-party data
- Users
	- Engineers
	- Data scientists
	- Product managers
	- Analysts, business users
- Easy and secure access to data with governance and transparency 
- Becoming subsumed into SageMaker Unified Studio
- Producers: S3, redshift, glue
- consumers: Athena, SageMarker, QuickSight

**Use Case**
- Catalog and discover data
	- Automated metadata management
- Govern data access
	- Fine-grained access controls
	- Governance workflows
- Collaborate across teams
	- Projects, shared analytics tools
- Automate workflows
	- Share data between producers and consumers

**Key Component**
- Domains
	- Organizational entities to group users, data, and projects
- Data portal
	- Web application, outside of AWS console
	- Catalog, discover, govern, share, analyze data
	- IAM authentication
- Business Data Catalog
	- Define taxonomy / glossary
- Data projects
	- Groups people, data sets, analytics tools
- Data environments
	- Provides infrastructure within projects (storage, analytics tools)
- Governance and access control
	- Built-in workflows for requesting data access and approving it
	- Manages permissions via Lake Formation, Redshift
