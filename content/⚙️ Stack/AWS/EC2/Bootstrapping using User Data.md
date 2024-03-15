# Bootstrapping using User Data

**Overall**

- script can be run once the instance is launched in a pre-configured state/ software install
- allows build automation
- user data
    - accessed via the meta-data IP (http://169.154.169.154/lastest/user-data)
    - limited to 16KB
    - can be modified when instance stopped
    - only executed once at launch
    - not secure - don’t use it for passwords/credentials
    - anything in user data is executed by the instance OS
    - runs as a shell script
    - procedural (run line by line)
- EC2 doesn’t interpret, the OS needs to understand the user data
- the instance will be launched and can be connected if it is badly configured (eg error)
- successfully configured ≠ correctly configured

**Boot-Time-To-Service-Time**

- AMI to instance takes short time only, where configuration can take mins-hrs in post launch time
- best way is to do most of these configuration during AMI baking

[[Bootstrapping using User Data/Untitled.png]]

**cloudformation (cfn::Init)**

- pass the complex bootstrapping instruction into an EC2 instance
- cfn::Init helper script - installed on EC2 OS
    - simple configuration management system
    - desired state (state what state you want to achieved and it help you to configure)
    - able to do packages, groups, users, sources, files, commands, services…
    - cloudformation initiate an EC2 and inject extra-info into user data
    - it can do stack update to update the physical resources

**CreationPolicy And Signals**

- added to a logical resource in the template, with a timeout value
- cloudformation waits until the cfn-signal that checks the resources reports to the stack
- if signal is correct the stack create successfully
- if not or timeout, the stack create with fail
