---
title: git rebase
tags:
  - git
---


- create new commits from other branch to current branch:
- use when new commits in master branch while working in feature branch
- DON'T rebase commit outside your own repo, because you will change commit history from others, causing merging conflict for everyone

From:
```
master: m1 -> m2 -> m3 
feature: m1 -> m2 -> f1 -> f2
```

rebase: () = new auto-generated commits
```
master: m1 -> m2 -> m3
feature: m1 -> m2 -> m3 -> (f1) -> (f2)  --pulled m3, create new f1 f2
```

Merge:
```
master: m1 -> m2 -> m3 -> (f1) -> (f2) 
feature: m1 -> m2 -> m3 -> (f1) -> (f2) --no conflict, f1 f2 are pushed
```

```
What Happens:
- remove all commits in the new feature
- rebase master to feature branch
- add new commits with the new feature
- merge rebased feature into master
```

rebase using the base from master, then extend the feature branch (current branch)
```
git rebase <master>
```

use branch_a as base, extend the branch with branch_b
```
git rebase <branch_a> <branch_b>
```

by using the interactive mode, we can edit the commit history in VIM and change order
```
git rebase -i HEAD~xxx
```

If you have other branchs sit on on the the branch being rebased. Those branch has to be rebase one by one manually as well. So use this instead:
```
git rebase -i main --update-refs
```
