
Let's say we have C1( main) >C2>C3 in linear, and we need to edit C2
1. git checkout C1 (main = C1)
2. git cherry-pick C2  (main = C2)
3. git commit --amend
4. git cherry-pick C3  (main = C3)