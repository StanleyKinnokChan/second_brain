Think of `check` like **unit tests** for your infra:
- They don’t replace configuration
- They **guard against misconfiguration**, drift, or future mistakes
- They validate **the outcome**, not just the intent

Example - check defined resources:
```
check "public_ip_check" {
  assert {
    condition     = aws_instance.web.associate_public_ip_address == false
    error_message = "Public IPs are not allowed"
  }
}
```

Example - check existing resource:
```
data "aws_ami" "ubuntu" {
  most_recent = true
  owners      = ["099720109477"] # Canonical

  filter {
    name   = "name"
    values = ["ubuntu/images/hvm-ssd/ubuntu-focal-20.04-amd64-server-*"]
  }
}

check "ami_check" {
  assert {
    condition     = data.aws_ami.ubuntu.owner_id == "099720109477"
    error_message = "The selected AMI is not from the official Canonical account"
  }

  assert {
    condition     = can(data.aws_ami.ubuntu.id)
    error_message = "AMI lookup failed; no matching image found"
  }
}
```