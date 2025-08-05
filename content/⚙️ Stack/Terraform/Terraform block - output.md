
By defining output block, you can access the values afterward:
- Display critical info
- Enable module integration and pass data between modules
- Automated workflow

Outputs are shown in the CLI after terraform has finishined its run
It stores in terraform state file and can be accessed again using `terraform output`


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

