---
title: git worktree
tags:
  - git
---


Workftree allows ones to edit another branch without stashing, good for
- Parallel Execution
- Comparison

1. Create a New Workspace
```
# in feature branch, want to fix a bug in main branch:
git worktree add ../hotfix-folder main

# this create a repo folder at the same level as as the current folder
```

2. Move to the New Workspace
```
# edit the branch
cd ../hotfix-folder
```

3. Cleanup
```
# Once you are done with the hotfix, you can return to your original directory and remove the temporary workspace:
cd ../my-original-repo
git worktree remove ../hotfix-folder
```