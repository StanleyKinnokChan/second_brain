---
title: SSH
tags:
  - git
---



window:

1. generate key pair
```
ssh-keygen -t ed25519 -C "stanleykinnok.chan@gmail.com"
```

2. Copy the Public Key to your Clipboard
```
# copy the whole things (method keystring email)
type C:\Users\Stanley\.ssh\id_ed25519.pub
```

3. Add the Key to GitHub (authentication key)

4. Switch your Local Repo to use SSH (git@.... instead of https://....)
```
git remote set-url origin git@github.com:StanleyKinnokChan/test-git-command.git
```

5. Test the Connection
```
# You should see a message saying: _"Hi StanleyKinnokChan! You've successfully authenticated..."
ssh -T git@github.com
```



