
The `data` block **fetches external data at plan time**, and passes it as **input (like a parameter)** to other blocks (usually `resource` blocks). It **doesn’t manage or change** the external resource — just reads its attributes for use elsewhere.

```

data "aws_ami" "amazon_linux" {
  most_recent = true
  owners      = ["amazon"]

  filter {
    name   = "name"
    values = ["amzn2-ami-hvm-*-x86_64-gp2"]
  }
}

resource "aws_instance" "web" {
  ami           = data.aws_ami.amazon_linux.id
  instance_type = "t2.micro"
}
```