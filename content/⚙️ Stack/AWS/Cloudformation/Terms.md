# Terms

- **template** = containing **logical resource** = what to create
- **stack** ⇒ by summiting the template to cloudformation, the stack will be created which to generate the **physical resource** corresponding to the logical resource in template (stack= deployment of template)
- **non-portable template** = limited to number of times applying the template, region and account to apply = hard code & not flexible
- **Common Component of a template**
    - metadata:
        - control the UI (eg label and parameter)
    - parameter:
        - eg EC2 type
    - description= what the template will be doing
    - resource part = mandatory
    - Condition: decision making
