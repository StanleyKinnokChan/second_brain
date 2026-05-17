---
title: Docker Volume & Bind mount
tags:
  - docker
---
Volume (managed by docker):
- Anonymous Volume
	- automatically created by docker when specify VOLUME ["/path/to/folder"] or -v s</path/to/folder> 
	- remove when the container is stopped
	- great for temp data and outsource the data storage to the host file system to increase performance
- Named Volume
	- specify -v <volume_name>:</path/to/folder> 
	- the volume persist after the container is stopped 
	- great for data which should be persistent but which you don't need to edit directly
	- can be shared to/ re-used by multiple containers
- Bind Mounts (managed by you) 
	- share your file/ folder in the local system to the containers
	- great for editable data, allows for instant updates without restarting the container
	- specify -v <abs/path/to/local/folder>:</path/to/folder> 
	- NOT USED FOR PRODUCTION
	- can be shared to/ re-used by multiple containers
	- 
If service used a name volume, volume must be defined (anonymous volume and bind mount is not needed) in the top level
```
services:
	foo:
		image: busybox
		volume: 
			- /app/data   # anonymous volume
			- data:/data/db   # named volume
			- /folder:/app   # bind mount

volumes:
	- data
```

When you see an "empty" block like `db_data: {}` (or just `db_data:` with nothing after it) in the top-level `volumes:` section, it means:

**"Create this volume using all the default settings."**
- 
- It creates a standard folder managed by [[Docker]] (usually in `/var/lib/docker/volumes/`) that stays there even if you stop or delete your containers.
```
volumes:
  db_data:
