---
title: git push
tags:
  - git
---



```
# update the default remote branch with current branch
git push

# update origin with branch_a
git pull origin branch_a

# update origin from source branch (local) to destination branch (remote)
git push origin <source>:<destination>

# update origin from source branch (local), create a branch New_destination that is not exist before
git push origin <source>:<New_destination>
```


mode:
- default: history must be the same as local and no new commit is made remote (no-risk)
- -f: overwrite the entire history anyway with the local (high rik)
- -force-with-lease: overwrite the history, but if there are new commit in the remote, stop pushing (low-risk)