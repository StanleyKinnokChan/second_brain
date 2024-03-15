
Put relative filepath inside gitignore file so that the git doesn't tract these files 


To ignore an entire directory with all its contents, you need to include the name of the directory with the slash `/` at the end:

```
test/
```


Sometimes .gitignore files don't work even though they're correct. The reason Git ignores files is that they are not added to the repository. If you added a file that you want to ignore before, it will be tracked by Git, and any skipping matching rules will be skipped. Git does this because the file is already part of the repository. To solve this, clear the cache before any commands
```
git rm -rf --cached .
git add .
```

