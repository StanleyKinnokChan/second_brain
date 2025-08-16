**git revert** should be used to undo changes on a public branch (create a new commit, which is a revert of the previous committed content). 

It should be used when it is remote branch that shares with others. 

Example
```
git revert HEAD~1
```

For simply remove the changes locally, see [[git reset]]