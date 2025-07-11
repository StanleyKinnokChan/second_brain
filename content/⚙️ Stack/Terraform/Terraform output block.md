

By defining output block, you can access the values afterward:

```
output "bucket_name" {
  value = aws_s3_bucket.bucket.bucket
}
```

```
#command
terraform output bucket_name

#result
stanawsbucket7425
```

It is useful, for example shell script or CI
```
BUCKET=$(terraform output -raw bucket_name)
```
