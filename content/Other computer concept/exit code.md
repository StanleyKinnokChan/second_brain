---
title: 
tags: []
---

An **exit code** (also called **exit status** or **return code**) is a number returned by a command or script when it finishes.

### Meaning:
- `0` → **Success** (command ran without errors)
- Non-zero (`1`, `2`, `127`, etc.) → **Failure** (different numbers mean different types of errors)

You can check the last command’s exit code using:
```
echo $?
```


Define output exit code:
```
#!/bin/bash
cp file.txt /some/path
if [ $? -ne 0 ]; then
  echo "Copy failed!"
  exit 1
fi
```