

![[Pasted image 20240307120811 1.png]]

[[git pull]] = git fetch + git merge

![[Pasted image 20240307120958 1.jpg]]

Sometimes the remote repo. has been updated by others and your own progress is behind. You also don't want to pull as it will replace your current working directory. As a result you:
- first use `git fetch origin/<branch>` download the remote repo to local repo
- Use `git diff origin/<branch>` to see the differences between working directory and the repo.
- Use `git add .` and `git commit -m "<msg>"` and `git commit origin/<branch>` to merge the files and manually correct the conflicts marker
- Use `git add .` and `git commit -m "<msg>"` and `git push -u origin/<branch>` to update the remote repo