---
title: 
tags:
  - Linux
---
### Login Shell

A **login shell** is the first shell session you get after logging in to a system. This happens when you log in at the console, use a command like `su -` to switch to another user, or connect remotely via SSH.

When a login shell starts, it reads and executes a specific set of configuration files to set up your environment. These are typically used for global settings that should only be run once per login session.

- It first reads the system-wide `/etc/profile` file. It's used by the system administrator to set global configurations for all users.
    
- Then, it looks for and executes the first of these user-specific files that it finds: 
	- `~/.bash_profile`
	- `~/.bash_login`
	- `~/.profile`

- If `~/.bash_profile` exists, it's the only one of the three that's sourced.
    
	**The Differences and Their Purpose**
	
	- **`~/.bash_profile`**: A user's personal startup file. This can be used to extend or override settings in the global configuration script. This is the file you should use for **Bash-specific commands** that should only be run once when you log in. It's the most common file for Bash users to configure their login environment. For example, you might set environment variables like `PATH` here. This usually used in sourcing `.bashrc`
	    
	- **`~/.bash_login`**: This file is a legacy alternative to `~/.bash_profile` that was created for compatibility with the C shell's `.login` file. It serves the same purpose as `~/.bash_profile` but is rarely used today. You should avoid creating this file to prevent it from being accidentally read instead of a more standard file.
	    
	- **`~/.profile`**: This file is a legacy alternative for the Bourne shell (`sh`) and other shells like the Korn shell (`ksh`). Because Bash is backward-compatible with the Bourne shell, it will read `~/.profile` if it doesn't find `~/.bash_profile` or `~/.bash_login`. You should use this file for **shell-agnostic settings** (like environment variables) that you want to be available to any POSIX-compliant shell, not just Bash
### Non-Login Shell

A **non-login shell** is any shell you start _after_ the initial login. This is the most common type of shell you'll encounter. It happens when you open a new terminal window in your graphical desktop environment or run a script.

Non-login shells don't read the same extensive set of startup files as login shells. They're designed to start faster and inherit most of their environment from the parent shell.

**`~/.bashrc`** is for settings that are not inherited by child shells and are specific to the interactive shell itself. It is a user's personal startup file. It can be used to extend or override settings in the global configuration script.

- It typically reads and executes the system-wide `/etc/bash.bashrc` file.
    
- Then, it reads and executes the user-specific `~/.bashrc` file.
