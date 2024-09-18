
#### Show all branch 
```
git branch -a
```

#### Switching branches
```
git checkout ＜branchname＞
```

#### Switching commit 
```
git checkout ＜branchname＞
```

#### Show all branch with hash ref
```
git show-ref
```

#### Create and switch to a new branch in a single step
```
git checkout -b ＜new-branch＞
```

#### Show current branch 
```
git rev-parse --abbrev-ref HEAD`
```

#### Forcefully move the branch to point to a specific commit
*This command can be **destructive**, as it moves the branch pointer to a new commit, potentially losing track of any commits*
```
git branch -f <branchname> <commit_hash>
```

