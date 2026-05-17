---
title: Terraform block - locals
tags:
  - terraform
---



- Use local values block to avoid repeating the same values, expressions or calculation multiple times in a configuration
- predefined the large map/ arrays/ transformation of variables that will be re-used
- recommend putting these in a separate file called `locals.tf` so they can be easily referenced
- access local values using the “**local.**” prefix followed by the local value name
e.g. 

1. **Basic String Concatenation**
```hcl
locals {
  # Simple name prefix combining project and environment
  name_prefix = "${var.project}-${var.environment}"
}

resource "aws_s3_bucket" "example" {
  bucket = "${local.name_prefix}-bucket"
}
```

2. **Simple Map for Tags**, making them easy to apply consistently across multiple resources
```hcl
locals {
  # Common tags in one place
  tags = {
    Project     = var.project
    Environment = var.environment
    Owner       = "DevOps"
  }
}

resource "aws_instance" "example" {
  ami           = "ami-123456"
  instance_type = "t2.micro"
  tags          = local.tags
}
```

3.  **Conditional Logic**
s
```hcl
locals {
  # Simple boolean check
  is_production = var.environment == "prod"
  
  # Set value based on environment
  instance_size = local.is_production ? "t2.medium" : "t2.micro"
}

resource "aws_instance" "server" {
  instance_type = local.instance_size
  ami           = "ami-123456"
}
```

4.  **Simple List Creation**
```hcl
locals {
  # Create a list of availability zones
  azs = ["us-west-2a", "us-west-2b", "us-west-2c"]
  
  # Get first two zones
  selected_azs = slice(local.azs, 0, 2)
}

resource "aws_subnet" "example" {
  count             = length(local.selected_azs)
  vpc_id            = aws_vpc.main.id
  availability_zone = local.selected_azs[count.index]
  cidr_block        = "10.0.${count.index}.0/24"
}
```

5. **Simple Map Transformation**
```hcl
locals {
  # Original map
  services = {
    web = { port = 80 }
    api = { port = 8080 }
  }
  
  # Add prefix to each key
  prefixed_services = {
    for name, config in local.services :
    "${var.project}-${name}" => config
  }
}
```


