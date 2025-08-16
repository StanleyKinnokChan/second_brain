
 **git reset** should be reserved for undoing changes on a private (local) branch (move back to previous commit, usually followed by a git add and git commit)
- --soft: change the [[HEAD]] reference to a previous specific commit, reset local tree only 
- (no flag): default, reset local tree and staging
- --hard: forces the [[HEAD]] to get back to that commit, reset local tree, staging and drive

#### IMPORTANT SHOUDN'T USE IT IN PUBLIC (SHARE BRANCH)
- because when every pulls the tree after reset, they will all miss the code
- use [[git revert]] instead

Good reference:
https://datacamp.com/tutorial/git-reset-revert-tutorial

bring back the deleted commit/ branch via `git reset head`
```
git reflog
git reset --hard <hash from reflog>
```