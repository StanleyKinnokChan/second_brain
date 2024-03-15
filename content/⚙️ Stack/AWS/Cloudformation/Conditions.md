# Conditions

- created in the optional ‘conditions’ section of a template
- conditions are evaluated to **true** or **false,** **before** resources are created
    - controlling if they are created or not
    - how many AZd to create resources
    - size of instances
    - …..
- use other intrinsic functions AND, EQUALS, IF, NOT, OR
- use with parameter → take the parameter for evaluating condition → do the actions if the condition included in the resources

eg create a EC2 and IP if the conditions ‘IsProd’ is true

[[Conditions/Untitled.png]]
