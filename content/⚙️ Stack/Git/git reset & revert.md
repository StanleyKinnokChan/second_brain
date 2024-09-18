**git revert** should be used to undo changes on a public branch (create a new commit, which is a revert of the previous committed content)

 **git reset** should be reserved for undoing changes on a private (local) branch (move back to previous commit, usually followed by a git add and git commit)
- --soft: change the [[HEAD]] reference to a previous specific commit, still keep every after that
- --hard: forces the [[HEAD]] to get back to that commit and deletes everything else after that


Good reference:
https://datacamp.com/tutorial/git-reset-revert-tutorial