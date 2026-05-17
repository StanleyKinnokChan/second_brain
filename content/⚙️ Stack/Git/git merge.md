---
title: git merge
tags:
  - git
---



# Merge type:
### Fast-forward
- When no additional commit in master, after feature branch was created
- merge moves head forward to the latest commit in the feature branch but does not create new commit

merge the current branch where the changes of all commits in feature branch squash into staging area in the current branch
```
git merge --squash <feature_branch>  
git commit
```

### Non Fast-Forward
##### recursive
- additional commit is auto created in master branch
```
git merge --no-ff  # not fastforward
```
##### octopus
##### ours
##### subtree


### [[git rebase]]



give up the merge
```
git merge --abort
```