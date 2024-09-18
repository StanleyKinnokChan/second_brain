
use branch_a as base, extend the branch with current branch
```
git rebase <branch_a>
```


use branch_a as base, extend the branch with branch_b
```
git rebase <branch_a> <branch_b>
```


by using the interactive mode, we can edit the commit history in VIM and change order
```
git rebase -i HEAD~xxx
```