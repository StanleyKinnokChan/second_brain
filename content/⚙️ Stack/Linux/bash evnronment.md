---
title: bash evnronment
tags:
  - linux
---

`/etc/profile`
When invoked interactively with the --login option or when invoked as sh, Bash reads the /etc/profile instructions. The Bash source contains sample profile files for general or individual use


`/etc/bashrc`
On systems offering multiple types of shells, it might be better to put Bash-specific configurations in this file, since /etc/profile is also read by other shells. 


`~/.bash_login`
This file contains specific settings that are normally only executed when you log in to the system. In the example, we use it to configure the umask value and to show a list of connected users upon login. This user also gets the calendar for the current month:

