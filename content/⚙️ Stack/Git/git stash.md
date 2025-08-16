
git stash can save up the progress of your current working directory and return to a clean directory as your local repo. 

- working directory & stage returns to the local repo
- the uncommit, unstaged changes stores in a internal memory -> stash
```
git stash --include-untracked # stash both new files and changes
git stash apply <number> # put the stash back to the clean directory (still in stash list)
git stash drop <number> # remove a stash
git stash pop # apply, but throws away the topmost stash (i.e. apply + drop)
git stash push -m "<comment>" # git stash apply but also add comment in list
git stash list # list of stash ever made in all commit

git stash clear # remove all stash
```
#### Use-case
Let's say you are developing new code and you got a call to repair the critical bug. Your code haven't been tested so you put it aside using `git stash`, fixed the bug and move your previous development progress back to your current working directory. 

#### Difference between `git stash pop` & `git stash apply`
`git stash pop` **throws away** the (topmost, by default) stash after applying it, whereas `git stash apply` **leaves it in the stash list** for possible later reuse (or you can then `git stash drop` it)