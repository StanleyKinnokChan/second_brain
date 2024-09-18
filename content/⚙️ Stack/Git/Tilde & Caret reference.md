- Tilde `~`  to go back a number of generations and always choosing the first parent of merge commits, commonly what you want.
- Caret `^` choose have two or more _immediate_ parents

>[!tip] Tips
> They can be used in chain

e.g. create a branch at 1 commit up from main, 2th parents, then 2 more commit up
```
git branch main~^2~2
```