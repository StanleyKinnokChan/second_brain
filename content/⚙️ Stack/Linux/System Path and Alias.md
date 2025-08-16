
The system path can be added by command line or [[bashrc file]]
```
export PATH="$PATH:/mnt/c/Users/StanleyChan/terraform"
Alias tf=terrafrom
```

By specifying the directory, the shell will receive the user input and find the executables with the exact the same name, for example:
- **Shell**: terraform
- **Action**: find the terraform.exe within terraform folder specified in the path. As there is alias, typing "tf" in the shell has the same effect as "terraform"