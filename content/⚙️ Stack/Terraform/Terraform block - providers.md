Providers allow Terraform to interact with cloud providers, SaaS providers, and other APIs.

A provider configuration is created using a `provider` block:
```
provider "google" {
  project = "acme-app"
  region  = "us-central1"
}
```

Use alias for multiple provider config (like multiple clouds/ regions/ accounts)
```
# The default provider configuration; resources that begin with `aws_` will use
# it as the default, and it can be referenced as `aws`.
provider "aws" {
  region = "us-east-1"
}

# Additional provider configuration for west coast region; resources can
# reference this as `aws.west`.
provider "aws" {
  alias  = "west"
  region = "us-west-2"
}
```

