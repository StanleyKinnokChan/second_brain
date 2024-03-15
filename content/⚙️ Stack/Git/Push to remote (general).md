# Push to remote (general)


1. go to the folder
2. `git init`
3. `git add .`
4. `git commit -m “commit”`
5. `git push -u -f origin main`

>[!tip] Tips
> -u flag add an upstream (tracking) reference to every branch that is pushed. You'll be able to use `git pull` and `git push` without argument afterward

> [!warning] Warn
> -f flag ignores the conflict and force to push the local repo to remote repo. Use it carefully
