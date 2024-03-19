
git stash can save up the progress of your current working directory and return to a clean directory as your local repo. 

#### Use-case
Let's say you are developing new code and you got a call to repair the critical bug. Your code haven't been tested so you put it aside using `git stash`, fixed the bug and move your previous development progress back to your current working directory. 

#### Difference between `git stash pop` & `git stash apply`
`git stash pop` **throws away** the (topmost, by default) stash after applying it, whereas `git stash apply` **leaves it in the stash list** for possible later reuse (or you can then `git stash drop` it)