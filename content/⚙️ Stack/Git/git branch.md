---
title: git branch
tags:
  - git
---


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
git state   # also show the files wait to be commited
git rev-parse --abbrev-ref HEAD    # only the branch name
```

#### Delete branch 
```
git branch -D <branch1> <branch2> ...
```

#### Forcefully move the branch to point to a specific commit
*This command can be **destructive**, as it moves the branch pointer to a new commit, potentially losing track of any commits*
```
git branch -f <branchname> <commit_hash>
```

