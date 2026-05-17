---
title: Terraform Built-In Function
tags:
  - terraform
---


Simplify infra code by providing built-in helper to manipulate strings, number, lists, etc.

Syntax: function_name(a1,a2,a3...)
Example: upper("hello")   returns "HELLO"
Example2: join("-", "hello", "terraform", "dev")   returns "hello-terraform-dev"

---
Some examples below:
#### Numeric Functions
e.g. min & max
Use-case
- dynamic resource allocation
- Automated calculations
#### String Functions
e.g. join, split, replace, base64encode, upper, lower
Use-case
- avoid repeatitive string handling
- transform string
#### Network Functions
e.g. cidrsubnet
Use-case
- Automate CIDR calculations
- Reduce manual errors
- scalable network design
#### Type Conversions
e.g. toset, tolist, tomap, tostring