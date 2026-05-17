---
title: git common command
tags:
  - git
---



Show the working tree status (current branch, untracted/ files in staging)
```
git status
```

Shows the commit logs.
```
git log
```

create and switch to new branch
```
git branch -b <new_branch>
```

check files in staging area
```
git ls-files
```

delete a file in staging area that already deleted in working dir
```
git remove <file_name>
```

remove unstaged changes in working dir back to the status of latest commit of the current branch
```
git checkout <file_name>  # use . if for all files
git restore <file_name> # same effect
```

unstage the stated changes (copy the latest commit into the stage)
```
git restore --stagsed <file_name> # same effect
```

undo commit
```
# undo commit
git reset --soft head~1 

# undo commit & stage
git reset head~1 

# undo commit & stage & working directory
git reset --hard head~1 
```

merge another branch into current branch
```
git merge <another_branch>
```


list all remote branch
```
git ls-remote
```