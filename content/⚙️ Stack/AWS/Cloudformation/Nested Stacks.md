# Nested Stacks

- resources in a single stack **share a lifecycle**
    - stack resource has a limit of 500)
    - can’t easily reuse resources e.g. a VPC
- Nested stacks
    - root stack & parent stack: within which you can create nested stack **by providing parameter** to that stack and **templateURL**, unless that stack has default parameters
    - output of that stack can be referenced in root stack by stackname.Outputs.xxxx
    - dependency relationship can be built among the stacks/ signalling
    - allow reuse of individual **template**/ **easy orchestration**
    - **use when everything is lifecycle linked/ sources limited**

    [[Nested Stacks/Untitled.png]]
