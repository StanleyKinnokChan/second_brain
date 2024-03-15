# Intrinsic functions

- **full name Fn::Sub:, short name !Sub in YAML)**
- allow the gain access to data at runtime
- can take action how things are when the template is being used to create stack

**Ref & Fn::GetATT:** reference a value from one logical resource or parameter in another one

**Fn::Join & Fn::Split:** join strings together as list or split them up ⇒ create web URL from EC2 IP

**Fn::GetAZs & Fn::Select:** get a list of AZ within a region where default VPS has subnets in that AZ and pick up one of these from list

**Conditions** (Fn::IF, And, Equals, Not & Or)

**Fn::Base64:** accept plaintext & output base64 text

**Fn::Sub:** allow you to substitute variables in the input based on runtime info (eg ${parameter/logicalresource/logicalresource.attname } )

**Fn::Cidr:** lets you build CIDR blocks for networking for automatic network configuration

[[Intrinsic functions/Untitled.png]]
