# AWS Control Tower

[[AWS Control Tower/Untitled.png]]

- quick & easy setup of multi-account environment
- orchestrates other AWS services to provide this functionality
- use organization, cloudformation, IAM identity centre…
- **landing zone** - multi-acc environment (**home region**)
    - built with AWS organization, config, cloudformation
    - **security OU** - log archive & audit accounts (cloudtrail & config logs)
    - **sandbox OU** - test/less rigid security
    - use **IAM identity centre** - sso, multiple- accs, ID federation
    - end user acc provisioning via **service catalog**
- **Guard rails -** rules for multi-acc governance
    - detect/ mandate rules/ standards across all accs
    - preventive - stop you doing things
    - detective - compliance checks (AWS config)
- **Account factory** - automates and stadardizes new acc creation
    - Guardrails are added automatically
    - cloud admins or end user
    - acc admin given to a named user
    - can be full integrated with a buinesses (Systems development life cycle), eg from testing to development
- dashboard - single page oversight of entire environment
